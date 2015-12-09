import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.HashSet;
import java.util.List;
import java.util.Map;
import java.util.Scanner;

import javax.swing.text.html.HTMLDocument.Iterator;


public class Palabras {

		
	/**
	 * @param args
	 * @throws FileNotFoundException 
	 */
	public static void main(String[] args) throws FileNotFoundException {
		// TODO Auto-generated method stub
//System.out.println(args[0]);
		HashMap<String,Integer> palabras = new HashMap<String, Integer>();
		HashMap<String,Integer> auxiliares = new HashMap<String, Integer>();

		Scanner sce = new Scanner(new File("stopwords-spanish.txt"));

		HashSet<String> spanishs = new HashSet<String>();
		
		while(sce.hasNext()){
			spanishs.add(sce.nextLine());
		}

	System.out.println();
String dat = args[0];
Scanner sc = new Scanner(new File(dat));
//		Scanner sc = new Scanner(System.in);
//BufferedReader sc = 
//        new BufferedReader(new InputStreamReader(System.in));   

		
		//System.out.println(sc.delimiter());
		//sc.useDelimiter(" |,|;|.|:|-|_|\\p{javaWhitespace}+");
		//System.out.println(sc.delimiter());	
		while(sc.hasNextLine()){
			
			String word = sc.nextLine();
		//	System.out.println(word);
			Scanner sc2 = new Scanner(word);
			sc2.useDelimiter(" |:|;|-|\\.|_|,|\\p{javaWhitespace}+|]|\\[|\\{|\\}|\\(|\\)|\\?|\\<|\\>");
			
			
			while(sc2.hasNext()){
				String p = sc2.next().toLowerCase();
				if(!(p.isEmpty())){
					Integer w = palabras.get(p);
					if(!spanishs.contains(p)){
						if(w == null){
							palabras.put(p, 1); //Si no hay palabras la agrega 
						}
						else{
							Integer cont = palabras.get(p);
							palabras.remove(p);
							palabras.put(p, cont+1);
						}
					}
				else{
					Integer w2 = palabras.get(p);
						if(w2 == null){
							auxiliares.put(p, 1); //Si no hay palabras la agrega 
						}
						else{
							Integer cont = auxiliares.get(p);
							auxiliares.remove(p);
							auxiliares.put(p, cont+1);
						}
				}
					
				}	
			}
		}	
		
		
		List<Element> elementos = new ArrayList<Element>();
		int suma = 0, i=0;
		
		for (String key : palabras.keySet()) {
			int j=0;
			suma += palabras.get(key);
		 	Element elemento = new Element(key,palabras.get(key));
		 	for(j=0; j<i; j++){
		 		if(!elementos.isEmpty()){
		 			if(elementos.get(j).getNumero() < elemento.getNumero()){
		 				Element aux =  elemento;
		 				elemento = elementos.get(j);
		 				elementos.remove(j);
		 				elementos.add(j, aux);
		 			}
		 		}
		 	}
		 	i++;
		 	elementos.add(j, elemento);
		 }
		int ConAux = 0;
		for (String key : auxiliares.keySet()) {
			ConAux += auxiliares.get(key);
			palabras.put(key, auxiliares.get(key));
		}
		System.out.println("Total de palabras es " + (suma+ConAux));
		System.out.println("Total de palabras sin auiliares  es " + suma);
		System.out.println("10 palabras mas comunes");
		for(int k=0, j=1; k<elementos.size(); k++,j++){
			System.out.println(j+ "  " + elementos.get(k).toString());
			if(j>=10) k = elementos.size() + 1;
		}
		System.out.println("\n\n");
		BufferedWriter bw = null;
		try {
			bw = new BufferedWriter(new FileWriter("reporte.txt"));
			bw.write("Total de palabras es " + (ConAux+suma) + "\n");
			bw.write("Total de palabras sin auxiliares " + suma + "\n");
			bw.write("10 palabras mas comunes" + "\n");
			for(int k=0, j=1; k<elementos.size(); k++,j++){
				bw.write(j + "  " + elementos.get(k).toString() + "\n");
				if(j>=10) k = elementos.size() + 1;
			}
			bw.write("\n");
			elementos = new ArrayList<Element>();
			i=0;
			for (String key : palabras.keySet()) {
				int j=0;
				suma += palabras.get(key);
			 	Element elemento = new Element(key,palabras.get(key));
			 	for(j=0; j<i; j++){
			 		if(!elementos.isEmpty()){
			 			if(elementos.get(j).getNumero() < elemento.getNumero()){
			 				Element aux =  elemento;
			 				elemento = elementos.get(j);
			 				elementos.remove(j);
			 				elementos.add(j, aux);
			 			}
			 		}
			 	}
			 	i++;
			 	elementos.add(j, elemento);
			 }
			for(int k=0; k<elementos.size(); k++){
				bw.write(elementos.get(k).toString() + "\n");
			}
			
			
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}finally {
			if(bw != null)
				try {
					bw.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
		}
		
		
		/*BufferedReader br = null;
		
		try {
			br = new BufferedReader(new FileReader("reporte.txt"));
			String currentLine;
				while((currentLine = br.readLine()) != null){
					System.out.println(currentLine);	
				}
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		finally {
			if(br != null)
				try {
					br.close();
				} catch (IOException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
		}*/
		
	}
}
