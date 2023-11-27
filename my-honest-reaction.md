# my honest reaction 150
#### oh god i despise java

[flag.class](https://github.com/gamer-1478/unreal-ctf/blob/main/flag.class)

Decomipling it with https://www.decompiler.com/ we get

```
import java.util.Scanner;

public class flag {
   public static void main(String[] var0) {
      String var1 = "5*Bg.)uH@DkcGn~(J'KOr6=X$7%ecad-s[a|3*wV~l8{z?)v{gbR8[%l]1WG0ouyp]#&ecB*yAj!k@rqnhQy!Ee|vW_sQH5f@nZb%KaCuI!k\\JVmiE{gq2b9AHS9Ge'`E\\pfr9$<J&{_*n8z!wsErnr$Me`@F28^va?0HK&e*?P';snYH0WpE}";
      char[] var2 = new char[100];
      int var3 = 0;

      for(int var4 = 6; var4 < var1.length(); var4 += 7) {
         var2[var3] = var1.charAt(var4);
         ++var3;
      }

      Scanner var6 = new Scanner(System.in);
      System.out.print("hi bbg enter pass: ");
      String var5 = var6.nextLine();
      if (var5.equals((new String(var2)).trim())) {
         System.out.println("good job!");
      } else {
         System.out.println("no lol");
      }

   }
}
    
```

just modify the script to print var2,
```
import java.util.Scanner;

public class flag {
   public static void main(String[] var0) {
      String var1 = "5*Bg.)uH@DkcGn~(J'KOr6=X$7%ecad-s[a|3*wV~l8{z?)v{gbR8[%l]1WG0ouyp]#&ecB*yAj!k@rqnhQy!Ee|vW_sQH5f@nZb%KaCuI!k\\JVmiE{gq2b9AHS9Ge'`E\\pfr9$<J&{_*n8z!wsErnr$Me`@F28^va?0HK&e*?P';snYH0WpE}";
      char[] var2 = new char[100];
      int var3 = 0;

      for(int var4 = 6; var4 < var1.length(); var4 += 7) {
         var2[var3] = var1.charAt(var4);
         ++var3;
      }

      Scanner var6 = new Scanner(System.in);
      System.out.print("hi bbg enter pass: ");
      System.out.print(var2);
      String var5 = var6.nextLine();
      if (var5.equals((new String(var2)).trim())) {
         System.out.println("good job!");
      } else {
         System.out.println("no lol");
      }

   }
}
    
```

you get the flag
```
flag - unreal{lucky_number_seven}
```
