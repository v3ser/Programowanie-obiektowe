package Zestaw3;
import java.util.ArrayList;
import java.util.Collections;
public class Zestaw3 {

    // Zadanie 0.
    // Napisz funkcję główną (main).
    public static void main(String[] args) {
        ArrayList<Integer> tab1 = new ArrayList<Integer>();
        ArrayList<Integer> tab2 = new ArrayList<Integer>();

        tab1.add(1);
        tab1.add(2);
        tab1.add(3);
        tab1.add(4);

        tab2.add(5);
        tab2.add(6);
        tab2.add(7);
        System.out.println(merge(tab1, tab2));
        System.out.println(mergeSorted(tab1,tab2));

        System.out.println(toArrayList("jes"));
        System.out.println(toArrayList(43242342));

        ArrayList<String> chars = toArrayList("tak");
        System.out.println(checkChar(chars, 'a'));
        System.out.println(checkChar(chars, 'x'));

        ArrayList<Integer> digits = toArrayList(1534534545);
        System.out.println(checkDigit(digits, 5));
        System.out.println(checkDigit(digits, 8));

        System.out.println(countChar(chars, 'a'));
        System.out.println(countDigit(digits, 4));

        System.out.println(uniqueArrayList(chars));
        System.out.println(uniqueArrayList2(digits));

        System.out.println(countArrayList(chars));
        System.out.println(countArrayList2(digits));
    }


    // Zadanie 1.
    // Napisz funkcję
    //		append(ArrayList<Integer> tab1, ArrayList<Integer> tab2),
    // która tworzy nową listę tablicową poprzez
    // dołączenie drugiej listy tablicowej do pierwszej.

    static ArrayList<Integer> append(ArrayList<Integer> tab1, ArrayList<Integer> tab2) {
        ArrayList<Integer> result = new ArrayList<Integer>();

        for (int i = 0; i < tab1.size(); i++) {
            result.add(tab1.get(i));
        }
        for (int element : tab2) {
            result.add(element);
        }
        return result;
    }

    // Zadanie 2.
    // Napisz funkcję
    //		merge(ArrayList<Integer> tab1, ArrayList<Integer> tab2),
    // która tworzy nową listę tablicową poprzez
    // dołączenie drugiej listy tablicowej do pierwszej w taki sposób,
    // że elementy wstawiane są na przemian. W przypadku, gdy skończą się
    // elementy jednej listy to do wyniku należy dołączyć pozostałe elementy.

    static ArrayList<Integer> merge(ArrayList<Integer> tab1, ArrayList<Integer> tab2) {
        ArrayList<Integer> result = new ArrayList<Integer>();
        int i = 0;
        int j = 0;
        while (i < tab1.size() && j < tab2.size()) {
            result.add(tab1.get(i));
            result.add(tab2.get(j));

            i++;
            j++;
        }

        while (i < tab1.size()) {
            result.add(tab1.get(i));
            i++;
        }
        while (i < tab2.size()) {
            result.add(tab2.get(j));
            j++;
        }
        return result;
    }


    // Zadanie 3.
    // Napisz funkcję
    //		mergeSorted(ArrayList<Integer> tab1, ArrayList<Integer> tab2),
    // która tworzy nową listę tablicową poprzez
    // dołączenie drugiej listy tablicowej do pierwszej w taki sposób,
    // że elementy wstawiane są w porządku rosnącym.

    public static ArrayList<Integer> mergeSorted(ArrayList<Integer> tab1, ArrayList<Integer> tab2) {
        ArrayList<Integer> result = new ArrayList<>();
        int i = 0, j = 0;
        int n1 = tab1.size();
        int n2 = tab2.size();
        while (i < n1 && j < n2) {
            if (tab1.get(i) <= tab2.get(j)) {
                result.add(tab1.get(i));
                i++;
            } else {
                result.add(tab2.get(j));
                j++;
            }
        }
        while (i < n1) {
            result.add(tab1.get(i));
            i++;
        }
        while (j < n2) {
            result.add(tab2.get(j));
            j++;
        }
        return result;
    }

    // Zadanie 4.
    // Napisz funkcje
    //		toArrayList(String napis)
    //		toArrayList(int liczba),
    // które z napisu/liczby tworzą listę tablicową posortowanych rosnąco znaków/cyfr.

    static ArrayList<String> toArrayList(String napis){
        ArrayList<String> result = new ArrayList<>();
        for(char c : napis.toCharArray()){
            result.add(String.valueOf(c));
        }
        Collections.sort(result);
        return result;
    }

    static ArrayList<Integer> toArrayList(int liczba){
        ArrayList<Integer> result = new ArrayList<>();
        String s = String.valueOf(liczba);
        for(char c : s.toCharArray()){
            result.add(Character.getNumericValue(c));
        }
        Collections.sort(result);
        return result;
    }

    // Zadanie 5.
    // Napisz funkcje
    //		checkChar(ArrayList<String> tab, char znak)
    // 		checkDigit(ArrayList<Integer> tab, int cyfra),
    // które sprawdzają czy podany znak/cyfra jest w liście
    // tablicowej z zadania 4 i zwracają true lub false.

    static boolean checkChar(ArrayList<String> tab, char znak){
        return tab.contains(String.valueOf(znak));
    }

    static boolean checkDigit(ArrayList<Integer> tab, int cyfra){
        return tab.contains(cyfra);
    }


    // Zadanie 6.
    // Napisz funkcje
    //		countChar(ArrayList<String> tab, char znak)
    // 		countDigit(ArrayList<Integer> tab, int cyfra),
    // które zliczają występowanie podanego znaku/cyfry
    // w liście tablicowej z zadania 4 i zwracają ilość zliczonych elementów.

    static int countChar(ArrayList<String> tab, char znak){
        int count = 0;
        for(String s : tab){
            if(s.equals(String.valueOf(znak))) count++;
        }
        return count;
    }

    static int countDigit(ArrayList<Integer> tab, int cyfra){
        int count = 0;
        for(int i : tab){
            if(i == cyfra) count++;
        }
        return count;
    }

    // Zadanie 7.
    // Napisz funkcje
    //		uniqueArrayList(ArrayList<String> tab)
    // 		uniqueArrayList(ArrayList<Integer> tab),
    // które tworzą dwuwymiarową listę tablicową unikalnych wartości,
    // a każda z wartości ma przyporządkowane 0.
    // Przykład: tab=[1,4,5,5,7,7] wynik -> [[1,0], [4,0], [5,0], [7,0]]

    static ArrayList<ArrayList<String>> uniqueArrayList(ArrayList<String> tab){
        ArrayList<ArrayList<String>> result = new ArrayList<>();
        ArrayList<String> unique = new ArrayList<>();
        for(String s: tab){
            if(!unique.contains(s)) unique.add(s);
        }
        Collections.sort(unique);
        for(String s: unique){
            ArrayList<String> pair = new ArrayList<>();
            pair.add(s);
            pair.add("0");
            result.add(pair);
        }
        return result;
    }
    static ArrayList<ArrayList<Integer>> uniqueArrayList2(ArrayList<Integer> tab){
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        ArrayList<Integer> unique = new ArrayList<>();
        for(int i: tab){
            if(!unique.contains(i)) unique.add(i);
        }
        Collections.sort(unique);
        for(int i: unique){
            ArrayList<Integer> pair = new ArrayList<>();
            pair.add(i);
            pair.add(0);
            result.add(pair);
        }
        return result;
    }

    // Zadanie 8.
    // Napisz funkcje
    // 		countArrayList(ArrayList<String> tab)
    // 		countArrayList(ArrayList<Integer> tab),
    // które tworzą dwuwymiarową listę tablicową, w której
    // zliczana jest ilość występujących cyfry/znaków z tablic z zadania 4
    // Przykład: tab=[1,4,5,5,7,7] wynik -> [[1,1], [4,1], [5,2], [7,2]]

    static ArrayList<ArrayList<String>> countArrayList(ArrayList<String> tab){
        ArrayList<ArrayList<String>> result = new ArrayList<>();
        ArrayList<String> unique = new ArrayList<>();
        for(String s : tab){
            if(!unique.contains(s)) unique.add(s);
        }
        Collections.sort(unique);
        for(String s : unique){
            int count = 0;
            for(String t: tab){
                if(t.equals(s)) count++;
            }
            ArrayList<String> pair = new ArrayList<>();
            pair.add(s);
            pair.add(String.valueOf(count));
            result.add(pair);
        }
        return result;
    }

    static ArrayList<ArrayList<Integer>> countArrayList2(ArrayList<Integer> tab){
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        ArrayList<Integer> unique = new ArrayList<>();
        for(int i : tab){
            if(!unique.contains(i)) unique.add(i);
        }
        Collections.sort(unique);
        for(int i : unique){
            int count = 0;
            for(int t: tab){
                if(t==i) count++;
            }
            ArrayList<Integer> pair = new ArrayList<>();
            pair.add(i);
            pair.add(count);
            result.add(pair);
        }
        return result;
    }



