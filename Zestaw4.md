import java.util.ArrayList;
import java.util.List;

class Produkt {
    private String nazwa;
    private double cena;
    private int iloscNaMagazynie;

    public Produkt(String nazwa, double cena, int iloscNaMagazynie) {
        this.nazwa = nazwa;
        this.cena = cena;
        this.iloscNaMagazynie = iloscNaMagazynie;
    }

    public void wyswietlInformacje() {
        System.out.println("Produkt: " + nazwa + ", Cena: " + cena + ", Ilość na magazynie: " + iloscNaMagazynie);
    }

    public void dodajDoMagazynu(int ilosc) {
        iloscNaMagazynie += ilosc;
    }

    public boolean usunZMagazynu(int ilosc) {
        if (iloscNaMagazynie >= ilosc) {
            iloscNaMagazynie -= ilosc;
            return true;
        } else {
            System.out.println("Brak wystarczającej ilości produktu " + nazwa);
            return false;
        }
    }

    public String getNazwa() { return nazwa; }
    public double getCena() { return cena; }
    public int getIloscNaMagazynie() { return iloscNaMagazynie; }
}

class KoszykZakupowy {
    private List<Produkt> produkty = new ArrayList<>();

    public void dodajProdukt(Produkt produkt, int ilosc) {
        if (produkt.usunZMagazynu(ilosc)) {
            for (int i = 0; i < ilosc; i++) {
                produkty.add(produkt);
            }
            System.out.println("Dodano " + ilosc + " x " + produkt.getNazwa() + " do koszyka.");
        }
    }

    public void wyswietlZawartoscKoszyka() {
        System.out.println("Zawartość koszyka:");
        produkty.stream()
                .map(Produkt::getNazwa)
                .distinct()
                .forEach(n -> {
                    long count = produkty.stream().filter(p -> p.getNazwa().equals(n)).count();
                    System.out.println(n + " - " + count + " szt.");
                });
    }

    public double obliczCalkowitaWartosc() {
        return produkty.stream().mapToDouble(Produkt::getCena).sum();
    }

    public List<Produkt> getProdukty() { return produkty; }

    public void usunProdukt(Produkt produkt, int ilosc) {
        int removed = 0;
        for (int i = 0; i < produkty.size() && removed < ilosc; i++) {
            if (produkty.get(i).equals(produkt)) {
                produkty.remove(i);
                i--;
                removed++;
            }
        }
    }
}

class Platnosc {
    private double kwota;
    private String statusPlatnosci; // np. "Oczekuje", "Opłacone"

    public Platnosc(double kwota) {
        this.kwota = kwota;
        this.statusPlatnosci = "Oczekuje";
    }

    public void zaplac() {
        this.statusPlatnosci = "Opłacone";
        System.out.println("Płatność zrealizowana. Kwota: " + kwota + " zł");
    }

    public String getStatusPlatnosci() {
        return statusPlatnosci;
    }

    public double getKwota() {
        return kwota;
    }
}

class Zamowienie {
    private KoszykZakupowy koszykZakupowy;
    private String statusZamowienia;
    private Platnosc platnosc;

    public Zamowienie(KoszykZakupowy koszykZakupowy, String statusZamowienia) {
        this.koszykZakupowy = koszykZakupowy;
        this.statusZamowienia = statusZamowienia;
        this.platnosc = new Platnosc(koszykZakupowy.obliczCalkowitaWartosc());
    }

    public void ustawStatusZamowienia(String status) {
        this.statusZamowienia = status;
    }

    public void wyswietlZamowienie() {
        System.out.println("Zamówienie (" + statusZamowienia + "):");
        koszykZakupowy.wyswietlZawartoscKoszyka();
        System.out.println("Łączna wartość: " + koszykZakupowy.obliczCalkowitaWartosc() + " zł");
        System.out.println("Status płatności: " + platnosc.getStatusPlatnosci());
    }

    public void finalizujZamowienie() {
        if (platnosc.getStatusPlatnosci().equals("Opłacone")) {
            statusZamowienia = "Gotowe do wysyłki";
            System.out.println("Zamówienie zostało sfinalizowane i jest gotowe do wysyłki!");
        } else {
            System.out.println("Nie można sfinalizować zamówienia — płatność nie została dokonana.");
        }
    }

    public void zwrocProdukt(Produkt produkt, int ilosc) {
        produkt.dodajDoMagazynu(ilosc);
        koszykZakupowy.usunProdukt(produkt, ilosc);
        System.out.println("Zwrócono " + ilosc + " szt. produktu " + produkt.getNazwa() + " do magazynu.");
    }

    public Platnosc getPlatnosc() {
        return platnosc;
    }

    public double getWartoscZamowienia() {
        return koszykZakupowy.obliczCalkowitaWartosc();
    }
}

class Klient {
    private String imie;
    private String nazwisko;
    private List<Zamowienie> listaZamowien = new ArrayList<>();

    public Klient(String imie, String nazwisko) {
        this.imie = imie;
        this.nazwisko = nazwisko;
    }

    public void dodajZamowienie(Zamowienie zamowienie) {
        listaZamowien.add(zamowienie);
    }

    public void wyswietlHistorieZamowien() {
        System.out.println("Historia zamówień klienta " + imie + " " + nazwisko + ":");
        for (Zamowienie z : listaZamowien) {
            z.wyswietlZamowienie();
        }
    }

    public double obliczLacznyKosztZamowien() {
        return listaZamowien.stream().mapToDouble(Zamowienie::getWartoscZamowienia).sum();
    }
}

class Sklep {
    private List<Produkt> produkty = new ArrayList<>();

    public void dodajProdukt(Produkt produkt) {
        produkty.add(produkt);
    }

    public void wyswietlProdukty() {
        System.out.println("Produkty w sklepie:");
        for (Produkt p : produkty) {
            p.wyswietlInformacje();
        }
    }

    public Produkt wyszukajProdukt(String nazwa) {
        return produkty.stream()
                .filter(p -> p.getNazwa().equalsIgnoreCase(nazwa))
                .findFirst()
                .orElse(null);
    }

    public void zakupy(Klient klient, String nazwaProduktu, int ilosc) {
        Produkt produkt = wyszukajProdukt(nazwaProduktu);
        if (produkt != null) {
            KoszykZakupowy koszyk = new KoszykZakupowy();
            koszyk.dodajProdukt(produkt, ilosc);
            Zamowienie zamowienie = new Zamowienie(koszyk, "W realizacji");
            klient.dodajZamowienie(zamowienie);
        } else {
            System.out.println("Produkt " + nazwaProduktu + " nie został znaleziony.");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Sklep sklep = new Sklep();
        sklep.dodajProdukt(new Produkt("Chleb", 5.0, 20));
        sklep.dodajProdukt(new Produkt("Mleko", 4.5, 15));
        sklep.dodajProdukt(new Produkt("Masło", 8.0, 10));

        Klient klient = new Klient("Jan", "Kowalski");

        sklep.zakupy(klient, "Chleb", 2);
        sklep.zakupy(klient, "Masło", 1);

        klient.wyswietlHistorieZamowien();

        Zamowienie zam = klient.obliczLacznyKosztZamowien() > 0 ? klient.obliczLacznyKosztZamowien() > 0 ? klient.listaZamowien.get(0) : null : null;
        if (zam != null) {
            zam.getPlatnosc().zaplac();
            zam.finalizujZamowienie();
        }

        System.out.println("\nPo finalizacji:");
        klient.wyswietlHistorieZamowien();
    }
}
