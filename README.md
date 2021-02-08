# caesar
package caesar;


import java.io.*;
import java.util.Scanner;
public class cryptage
{
static String  directory = System.getProperty("user.home");
static  String   fileName = "A.txt";
static String   absolutePath = directory + File.separator + fileName;
 public static void main(String [] arg)
 {
     char alphabet []={'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'};
  String chaine = "abcdefghijklmnopqrstuvwxyz ABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890/*-+&éèêëûùüïî$£()ç%";
  String crypte="";
  int lu, k, lchaine, posChaine;
  char carLu,carChaine ;
  Scanner c=new Scanner(System.in);
     System.out.println("entrer  le clé k ");
     k=c.nextInt();
 // lchaine = chaine.length();
System.out.println("entrer le message ");
String m=c.nextLine();
while(m.equals("")){
    
 m=c.nextLine();
}
 
 int p;
 for(int j=0;j<m.length();j++)
 for(int i=0;i<alphabet.length;i++)
 {
 if(m.charAt(j)==alphabet[i]){
 p=(i+k)%26;
 crypte= crypte+alphabet[p];
 }
}
 // sauvgarder dans a.txt
 try(BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(absolutePath))) {
    String fileContent = crypte;
    bufferedWriter.write(fileContent);
} catch (IOException e) {
    // Exception handling
}
     System.out.println("text crypté:   "+crypte);
 


//read file
     String text="";
    try(BufferedReader bufferedReader = new BufferedReader(new FileReader(absolutePath))) {
    String line = bufferedReader.readLine();
    while(line != null) {
        text=text+line;
        line = bufferedReader.readLine();
    }
} catch (FileNotFoundException e) {
    // Exception handling
} catch (IOException e) {
    // Exception handling
} 
     
     
     
     
// decryptage  
String decrypt="";
 for(int j=0;j<text.length();j++)
 for(int i=0;i<alphabet.length;i++)
 {
 if(text.charAt(j)==alphabet[i]){
 p=(i-k)%26;
 if(p<0){
 p=p+26;}
 decrypt= decrypt+alphabet[p];
 }
}
 //sauvgarder dans B.txt
 fileName = "B.txt";
absolutePath = directory + File.separator + fileName;
  try(BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(absolutePath))) {
    String fileContent = decrypt;
    bufferedWriter.write(fileContent);
} catch (IOException e) {
    // Exception handling
}
     System.out.println("text décrypté:   "+decrypt);
 
 
}}
