# Java-Invoice-

package com.company;
import java.util.ArrayList;
import java.util.Scanner;


public class Main {
    public static void main(String args[]) {

        //creating ArrayLists
        ArrayList<String> products = new ArrayList<String>();
        ArrayList<Double> prices = new ArrayList<Double>();

        //taking input from user
        Scanner input = new Scanner(System.in);

        //Adding products and prices
        products.add("Bison Sweater");
        prices.add(55.99);
        products.add("Bison Tee");
        prices.add(14.99);
        products.add("Bison Hoodie");
        prices.add(23.99);
        products.add("Bison Bumpersticker");
        prices.add(4.99);

        String answer = "";
        ArrayList<String> purchases = new ArrayList<String>();

        do {
            System.out.println("What do you want to do?");
            System.out.println("1) add purchase 2) change purchase 3) show purchases 4) finish transaction");

            answer = input.nextLine();
            if (answer.equals("1"))
            {
                System.out.println("What do you wish to buy?");
                answer = input.nextLine();
                purchases.add(answer);
            }

            //adding option to change the purchase
            else if (answer.equals("2"))
            {
                //takes item that the user want to change
                System.out.println("What purchase you want to change?");
                String change = input.nextLine();

                //change to new purchase
                System.out.println("What you want to change with?");
                String changewith = input.nextLine();

                purchases.set(purchases.indexOf(change), changewith);
            }

            //displaying the purchases information
            else if (answer.equals("3"))
            {
                for(int i = 0; i < purchases.size(); i++)
                {
                    System.out.println(purchases.get(i));
                }
            }
        } while (! answer.equals("4"));

        //calculating total cost
        double totalcost = 0.0;
        int j = 0;
        for (int i = 0; i < purchases.size(); i++)
        {
            j=0;
            do {

                // condition is check if the value in purchases at position i is equal to the value in products at position j
                if (purchases.get(i).equals(products.get(j)) )
                {

                    // increment totalcost with the ith value in the prices array
                    totalcost = totalcost + prices.get(j);
                }
                j++;
            } while (j < products.size());
        }
        System.out.println("Total Cost: "+totalcost);
    }
}
