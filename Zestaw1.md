package Zestaw1;
import java.awt.*;
import java.util.Scanner;
public class Zestaw1 {

    // Zadanie 0.
    // Napisz funkcję główną (main).
    public static void main(String[] args){
        System.out.println(zadanie_30(30));
    }


    // Zadanie 1.
    // Wypisz swoje imię i nazwisko na ekranie.
        static void zadanie_1(){
        String imie = "Marcin Rawa";
        System.out.println(imie);

    }


    // Zadanie 2.
    // Wypisz długość imienia i nazwiska.

    static void zadanie_2(){
        String firstName = "Marcin";
        String lastName = "Rawa";
        System.out.println("Dlugosc imienia " + firstName.length());
        System.out.println("Dlugosc nazwiska " + lastName.length());

    }

    // Zadanie 3.
    // Za pomocą printf połącz 3 wyrazy "Ala" "ma" "kota"
    // w jeden i wyświetl go na ekranie.

    static void zadanie_3(){
        System.out.printf("Ala ma kota");

    }

    // Zadanie 4.
    // W zdaniu „Ala ma kota” zastąp
    // wszystkie litery „a” literą „e”.

    static void zadanie_4(){
        String text = "Ala ma Kota";
        System.out.println(text.replace("a", "e"));

    }

    // Zadanie 5.
    // Napisz program, który będzie pobierał dwa słowa
    // od użytkownika i wypisywał je na ekranie.

    static void zadanie_5(){
        Scanner slowo1 = new Scanner(System.in);
        System.out.print("Podaj pierwsze slowo ");
        String slowo_1 = slowo1.nextLine();

        Scanner slowo2 = new Scanner(System.in);
        System.out.print("Podaj drugie slowo ");
        String slowo_2 = slowo1.nextLine();

        System.out.print(slowo_1 + " " + slowo_2);





    }

    // Zadanie 6.
    // Napisz program, który będzie pobierał dwie liczby od
    // użytkownika i wypisał ich sumę, różnicę, iloczyn i iloraz.

    static void zadanie_6(){
        Scanner liczba1 = new Scanner(System.in);
        System.out.print("Podaj liczbe 1: ");
        float liczba_1 = liczba1.nextFloat();

        Scanner liczba2 = new Scanner(System.in);
        System.out.print("Podaj liczbe 2: ");
        float liczba_2 = liczba2.nextFloat();

        System.out.println("Suma: "+(liczba_1 + liczba_2));
        System.out.println("Roznica: "+(liczba_1 - liczba_2));
        System.out.println("iloczyn: "+(liczba_1 * liczba_2));
        System.out.println("iloraz: "+(liczba_1 / liczba_2));



    }

    // Zadanie 7.
    // Napisz prostą aplikację kalkulatora tekstowego,
    // która przyjmuje dwa liczby od użytkownika jako wejście
    // i wykonuje podstawowe operacje matematyczne
    // (dodawanie, odejmowanie, mnożenie, dzielenie).
    // Wyświetl wyniki na ekranie.

    void zadanie_7(){

    }

    // Zadanie 8.
    // Napisz program, który będzie pobierał
    // liczbę x od użytkownika i wypisał tę liczbę:
    //      • Powiększoną o 140
    //      • Pomniejszoną o 31
    //      • Powiększoną 7 razy
    //      • Pomniejszoną 13 razy
    //      • Modulo 7
    //      • Część całkowita z dzielenia przez 4
    //      • Podniesioną do potęgi 45
    //      • Iloczyn bitowy z 67
    //      • Suma bitowa z 59
    //      • XOR z 23
    //      • Przesuniętą o 5 bitów w lewo
    //      • Przesuniętą o 6 bitów w prawo

    static void zadanie_8(){
        Scanner myObj = new Scanner(System.in);
        System.out.println(" Podaj liczbe x: ");
        int liczba1 = myObj.nextInt();

        System.out.println(liczba1+140);
        System.out.println(liczba1-31);
        System.out.println(liczba1*7);
        System.out.println(liczba1/13.0);
        System.out.println(liczba1%7);
        System.out.println(Math.floor(liczba1/4));
        System.out.println(Math.pow(liczba1,45));
        System.out.println(liczba1 & 67);
        System.out.println(liczba1|59);
        System.out.println(liczba1^23);
        System.out.println(liczba1<<5);
        System.out.println(liczba1>>6);



    }

    // Zadanie 9.
    // Napisz program, który sprawdza czy podana
    // liczba jest parzysta i wypisuje odpowiedni komunikat.

    static void zadanie_9(){
        Scanner myObj = new Scanner(System.in);
        System.out.println("Podaj liczbe: ");
        int liczba = myObj.nextInt();
        if(liczba%2==0){
            System.out.println("Liczba jest parzysta ");
        }
        else System.out.println("Liczba jest nie parzysta ");
    }

    // Zadanie 10.
    // Napisz program, który pobiera od użytkownika trzy liczby
    // i wypisuje je w kolejności rosnącej.

    static void zadanie_10(){
        Scanner  sc = new Scanner(System.in);
        System.out.print("Podaj a: ");
        int a = sc.nextInt();
        System.out.print("Podaj b: ");
        int b = sc.nextInt();
        System.out.print("Podaj c: ");
        int c = sc.nextInt();

        if(a>b){int t=a;a=b;b=t;}
        if(b>c){int t=b;b=c;c=t;}
        if(a>b){int t=a;a=b;b=t;}

        System.out.println(a+ " " + b + " " + c);


    }

    // Zadanie 11.
    // Napisz program, który pobiera od użytkownika trzy liczby
    // i wypisuje je w kolejności malejącej.

    static void zadanie_11(){
        Scanner  sc = new Scanner(System.in);
        System.out.print("Podaj a: ");
        int a = sc.nextInt();
        System.out.print("Podaj b: ");
        int b = sc.nextInt();
        System.out.print("Podaj c: ");
        int c = sc.nextInt();

        if(a<b){int t=a;a=b;b=t;}
        if(b<c){int t=b;b=c;c=t;}
        if(a<b){int t=a;a=b;b=t;}

        System.out.println(a+ " " + b + " " + c);


    }

    // Zadanie 12.
    // Napisz program, który rozwiązuje równanie liniowe ax + b = 0
    // o parametrach a i b podanych przez użytkownika.

    static void zadanie_12(){
        Scanner sc = new Scanner(System.in);
        System.out.print("Podaj a: ");
        float a = sc.nextFloat();
        System.out.print("Podaj b: ");
        float b = sc.nextFloat();
        System.out.println("x =" +(-b/a));

    }

    // Zadanie 13.
    // Napisz program, który pobiera od użytkownika wartości parametrów
    // a, b i c, i sprawdza czy można z nich zbudować trójkąt.

    static void zadanie_13(){
        Scanner sc = new Scanner(System.in);
        System.out.print("Podaj a: ");
        float a = sc.nextFloat();
        System.out.print("Podaj b: ");
        float b = sc.nextFloat();
        System.out.print("Podaj c: ");
        float c = sc.nextFloat();
        if(((a+b) > c) && ((b+c) > a) && ((a+c) > b)) {
            System.out.println("Mozna zbudowa trojkat");
        }
        else System.out.print("Nie mozna zbudowac trojkata");
    }

    // Zadanie 14.
    // Napisz program, który pobiera od użytkownika wartości parametrów
    // a, b i c, które powinny być bokami pewnego trójkąta
    // i sprawdza czy trójkąt jest ostrokątny, prostokątny czy rozwartokątny.

    static void zadanie_14(){
        Scanner sc = new Scanner(System.in);
        System.out.print("Podaj a: ");
        float a = sc.nextFloat();
        System.out.print("Podaj b: ");
        float b = sc.nextFloat();
        System.out.print("Podaj c: ");
        float c = sc.nextFloat();

        if(((a+b) > c) && ((b+c) > a) && ((a+c) > b)) {
            if (a * a + b * b > c * c) {
                System.out.print("Trojkat jest ostrokatny");
            } else if (a * a + b * b == c * c) {
                System.out.print("Trojkat jest prostokatny");
            } else {
                System.out.print("Trojkat jest rozwartokatny");
            }
        }else {
            System.out.print("Nie mozna zbudowac trojkata");
            }
    }


    // Zadanie 15.
    // Napisz program, który pobiera od użytkownika liczbę m oraz n
    // i zwraca resztę z dzielenia m przez n.

    static int zadanie_15(){
        Scanner sc = new Scanner(System.in);
        System.out.print("Podaj m: ");
       int m = sc.nextInt();
        System.out.print("Podaj n: ");
        int n = sc.nextInt();
        return m%n;
    }

    // Zadanie 16.
    // Napisz program, który oblicza podatek należny
    // na podstawie kwoty dochodu podanej przez użytkownika
    // i następujących progów podatkowych:
    //      Kwota wolna od podatku: 30 000 zł
    //      I próg podatkowy: do 120 000 zł stawka 12%
    //      II próg podatkowy: od 120 000 zł stawka 32%
    //      Danina solidarnościowa: od 1 000 000 zł stawka 4%
    // Kwota zmniejszająca podatek wynosi 3 600 zł.

    static void zadanie_16(){
        Scanner sc = new Scanner(System.in);
        System.out.print("Podaj dochod: ");
        double dochod = sc.nextDouble();
        double podatek = 0.0;
        double kwotaWolna = 30000;
        double prog1 = 120000;
        double danina = 1000000;
        double zmniejszeniePodatku = 3600;

        if (dochod <= kwotaWolna) {
            podatek = 0.0;
        } else if (dochod <= prog1) {
            podatek = (dochod - kwotaWolna) * 0.12;
        } else {
            podatek = (prog1 - kwotaWolna) * 0.12;
            podatek += (Math.min(dochod, danina) - prog1) * 0.32;
        }
        if (dochod > danina) {
            podatek += (dochod - danina) * 0.04;
        }
        podatek -= zmniejszeniePodatku;
        if (podatek < 0) {
            podatek = 0.0;
        }

        System.out.printf("Należny podatek: %.2f zł%n", podatek);
    }





    // Zadanie 17.
    // Napisz program, który pobiera od użytkownika liczbę n
    // i wypisze dla długości boków od 1 do n
    // wszystkie trójki pitagorejskie.

    void zadanie_17(){
        Scanner scanner = new Scanner(System.in);
        System.out.print("Podaj maksymalną długość boku (n): ");
        int n = scanner.nextInt();
        System.out.println("Trójki pitagorejskie o bokach od 1 do " + n + ":");
                for (int a = 1; a <= n; a++) {
                    for (int b = a; b <= n; b++) {
                        for (int c = b; c <= n; c++) {
                            if (a * a + b * b == c * c) {
                                System.out.println(a + ", " + b + ", " + c);
                            }
                        }
                    }
                }
            }



    // Zadanie 18.
    // Napisz program, który pobiera od użytkownika liczbę n
    // i wypisze wszystkie liczby pierwsze od 2 do n.

    static void zadanie_18(){
        Scanner sc = new Scanner(System.in);
        System.out.print("Podaj n: ");
        int n = sc.nextInt();

        for(int i=2; i<=n;i++){
            boolean flaga = true;
            for(int j=2;j<i;j++){
                if(i%j == 0){
                    flaga = false;
                    break;

                }
            }
            if(flaga){
                System.out.println(i);
            }
        }

    }

    // Zadanie 19.
    // Napisz program, który pobiera od użytkownika liczbę m i n,
    // a następnie wypisze wszystkie liczby m-cyfrowe,
    // które podzielne są przez n.

    static void zadanie_19(){
        Scanner sc = new Scanner(System.in);
        System.out.print("Podaj m: ");
        int m = sc.nextInt();
        System.out.print("Podaj n: ");
        int n = sc.nextInt();

        int start = (int)Math.pow(10,m - 1);
        int end = (int)Math.pow(10, m) - 1;

        for(int i =start;i<=end;i++){
            if(i%n == 0){
                System.out.println(i);
            }
        }


    }

    // Zadanie 20.
    // Napisz program, który wypisze piramidę z gwiazdek (*)
    // w dwóch wariantach, której wysokość jest liczbą n.
    // Program powinien przyjmować dwa argumenty - n (wysokość) i v (wariant).

    void zadanie_20(){

    }

    // Zadanie 21.
    // Napisz program, który obliczy i zwróci silnie liczby n.
    // Program powinien przyjmować jeden argument - liczbę n.

    static int zadanie_21(int n){
        int wynik = 1;
        for(int i = n; i > 1; i--){
            wynik += i;
        }

        return wynik;

    }

    // Zadanie 22.
    // Napisz program, który obliczy i zwróci silnie podwójną liczby n.
    // Program powinien przyjmować jeden argument - liczbę n.

    static int zadanie_22(int n){
        int wynik = 1;

        for(int i = n; i > 1; i-=2){
            wynik += i;
        }
        return wynik;

    }

    // Zadanie 23.
    // Napisz program, który obliczy i zwróci silnie m-tą liczby n.
    // Program powinien przyjmować dwa argumenty - liczbę m oraz n.

    static int zadanie_23(int m, int n){
        int wynik = 1;
        for(int i = n; i > 1; i-=m){
            wynik += i;
        }
        return wynik;

    }

    // Zadanie 24.
    // Napisz program, który obliczy i zwróci sumę n
    // kolejnych liczb naturalnych.
    // Program powinien przyjmować jeden argument - liczbę n.

    void zadanie_24(){

    }

    // Zadanie 25.
    // Napisz program, który obliczy i zwróci sumę n
    // kolejnych liczb parzystych.
    // Program powinien przyjmować jeden argument - liczbę n.

    void zadanie_25(){

    }

    // Zadanie 26.
    // Napisz program, który obliczy i zwróci sumę n
    // kolejnych liczb nieparzystych.
    // Program powinien przyjmować jeden argument - liczbę n.

    void zadanie_26(){

    }

    // Zadanie 27.
    // Napisz program, który obliczy i zwróci sumę n
    // liczb będących kwadratami kolejnych liczb naturalnych.
    // Program powinien przyjmować jeden argument - liczbę n.

    void zadanie_27(){

    }

    // Zadanie 28.
    // Napisz program, który obliczy i zwróci sumę n
    // liczb będących sześcianami kolejnych liczb naturalnych.
    // Program powinien przyjmować jeden argument - liczbę n.

    void zadanie_28(){

    }

    // Zadanie 29.
    // Napisz program, który obliczy i zwróci sumę n
    // liczb będących odwrotnościami kolejnych liczb naturalnych.
    // Program powinien przyjmować jeden argument - liczbę n.

    void zadanie_29(){

    }

    // Zadanie 30.
    // Napisz program, który sprawdza (prawda/fałsz)
    // czy liczba n jest doskonała.
    // Program powinien przyjmować jeden argument - liczbę n.

   static boolean zadanie_30(int n){
        int suma = 0;
        for(int i = 1; i < n; i++){
            if(n % i == 0){
                suma += i;

            }
        }
        return n == suma;
    }
}
