import java.io.*;
import java.io.FileReader;
import java.util.*;


public class movieGenres {
    public static void main(String[]args)throws IOException{
        File file= new File("movies.csv");
        BufferedReader reader= new BufferedReader(new FileReader(file));
        HashMap<String,Integer> mapYears= new HashMap<>();//this is a hashmap of the years.
        HashMap<String,Integer> map = new HashMap<>();//this a hasmap of the genres.
        HashMap<Integer,Integer> howMany = new HashMap<>();//this is a hasmap of how many movies came out.
        reader.readLine();
        String[]array;
        String line= reader.readLine();
        //Parses the CSV into just the movie genre and year released.
        while(line !=null){
            array=line.split(",");
            line=reader.readLine();


            try{
                //this is parsing for the year.
                int comma = line.lastIndexOf(',');
                String sub = line.substring(0,comma);
                int open = sub.lastIndexOf('(')+1;
                int close = sub.lastIndexOf(')');
                int year = Integer.parseInt(sub.substring(open,close));

                //this is checking the last five years of movies.

                if (year>=2015){
                    String[] genres = array[array.length-1].split("\\|");
                    //Adding the genres to the hashmap

                    for (String genre:genres){
                        if (mapYears.containsKey(genre)){
                            mapYears.put(genre,mapYears.get(genre)+1);
                        }
                        else{
                            mapYears.put(genre,1);
                        }
                    }

                }
                //Adding how many years to the hashmap
                if (howMany.containsKey(year)){
                    howMany.put(year,howMany.get(year)+1);
                }
                else{
                    howMany.put(year,1);
                }



            }

            catch (Exception e){

            }

            //this looks for the genres
            String[] genres = array[array.length-1].split("\\|");
            //checks to see if genre is in the hashmap
            for (String genre:genres){
                if (map.containsKey(genre)){
                    map.put(genre,map.get(genre)+1);
                }
                else{
                    map.put(genre,1);
                }
            }

        }
        //Sorting the movies and years.
        ArrayList<Map.Entry<String, Integer>> sorted = new ArrayList<>();
        ArrayList<Map.Entry<String,Integer>> sortedYears = new ArrayList<>();


        for (Map.Entry<String, Integer> entry : map.entrySet()){
            sorted.add(entry);

        }

        for (Map.Entry<String, Integer> entry : mapYears.entrySet()){
            sortedYears.add(entry);

        }
        //decending order
        sorted.sort((a, b) -> b.getValue().compareTo(a.getValue()));
        sortedYears.sort((a, b) -> b.getValue().compareTo(a.getValue()));

        System.out.println("All movies: ");

        for (Map.Entry<String, Integer> entry : sorted) {

            System.out.println(entry.getValue() + " instances of " + entry.getKey());
        }
        System.out.println("Movies in the last five years: ");

        for (Map.Entry<String, Integer> entry : sortedYears) {

            System.out.println(entry.getValue() + " instances of " + entry.getKey());
        }



        ArrayList<Map.Entry<Integer, Integer>> sortedd = new ArrayList<>();

        for (Map.Entry<Integer, Integer> entry : howMany.entrySet()){
            sortedd.add(entry);

        }
        //ascending order
        sortedd.sort((a, b) -> a.getKey().compareTo(b.getKey()));

        System.out.println("Movies per year: ");

        for (Map.Entry<Integer, Integer> entry : sortedd) {

            System.out.println(entry.getValue() + " movies in year " + entry.getKey());
        }

    }

}
