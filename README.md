
```
D1
C2
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        HashMap<String, Integer> cnt = new HashMap<>();
        cnt.put("PASS", 0);
        cnt.put("FAIL", 0);
        for(int i =0; i<n;i++){
            String name = sc.next();
            double score = sc.nextDouble();
            if(score >=5){
                cnt.put("PASS", cnt.get("PASS") +1);
            }
            else{
                cnt.put("FAIL", cnt.get("FAIL") +1);
            }
        }
        System.out.println("PASS " + cnt.get("PASS"));
            System.out.println("FAIL " + cnt.get("FAIL"));
    }
}

