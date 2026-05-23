
```
//De 1
    //C2
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
    //C5
        boolean any = list.stream().anyMatch(s -> s >= 9);

        boolean all = list.stream().allMatch(s -> s >= 5);

        boolean none = list.stream().noneMatch(s -> s < 0 || s > 10);

        System.out.println("ANY " + any);
        System.out.println("ALL " + all);
        System.out.println("NONE " + none);
    //C1
        // TODO
        if(score >= 8.5) return 4.0;
        if(score >= 7.0) return 3.0;
        if(score >= 5.5) return 2.0;
        if(score >= 4.0) return 1.0;
        // TODO
        ArrayList<Subject> list = new ArrayList<>();
        double totalPoint = 0;
        int totalCredit = 0;
        for(int i = 0; i < n; i++) {
            String code = sc.next();
            int credit = sc.nextInt();
            double score = sc.nextDouble();
            Subject s = new Subject(code, credit, score);
            list.add(s);
            totalPoint += credit * s.gradePoint();
            totalCredit += credit;
        }
        for(Subject s : list) {
            System.out.printf("%s %.1f\n", s.getCode(), s.gradePoint());
        }
        double gpa = totalPoint / totalCredit;
        System.out.printf("GPA %.2f\n", gpa);
    //C3
        // Ghi nhị phân
        DataOutputStream dos = new DataOutputStream(
            new FileOutputStream("ints.bin"));
        for (int i = 0; i < n; i++) {
            dos.writeInt(sc.nextInt());
        }
        dos.close();

        // Đọc lại, tìm min/max
        DataInputStream dis = new DataInputStream(
             new FileInputStream("ints.bin"));
        int min = Integer.MAX_VALUE;
        int max = Integer.MIN_VALUE;
        try {
            while (true) {
                int x = dis.readInt();
                if (x < min) min = x;
                if (x > max) max = x;
            }
        } catch (EOFException e) {
        }
        dis.close();
        System.out.println("min: " + min);
        System.out.println("max: " + max);

//De 2
    //C2
        for(int i =0;i<n;i++){
                a.add(sc.nextInt());
            }
            Collections.reverse(a);
            for(int i =0;i<n;i++){
                System.out.print(a.get(i)+" ");
            }
    //C3
        import java.io.*;
        import java.util.*;
        public class Main {
            public static void main(String[] args) throws Exception {
                Scanner sc = new Scanner(System.in);
                int n = sc.nextInt();
                DataOutputStream dos = new DataOutputStream(
                        new FileOutputStream("double.dat"));
                for (int i = 0; i < n; i++) {
                    dos.writeDouble(sc.nextDouble());
                }
                dos.close();
                DataInputStream dis = new DataInputStream(
                        new FileInputStream("double.dat"));
                double sum = 0;
                try {
                    while (true) {
                        sum += dis.readDouble();
                    }
                } catch (EOFException e) {
                }
                dis.close();
                double avg = sum / n;
                System.out.printf("Average: %.2f%n", avg);
             }
        }
    //C1
        abstract class Employee {
        //
        private String name;
        private LocalDate started;
        public Employee(String name, LocalDate started) {
            this.name = name;
            this.started = started;
        }
        public String getName() {
            return name;
        }
        public LocalDate getStarted() {
            return started;
        }
        public void setName(String name) {
            this.name = name;
        }
        public void setStarted(LocalDate started) {
            this.started = started;
        }
        abstract void showInfo();
        abstract double calcSalary();
        //
        }

        class FullTimeEmployee extends Employee {
        //
        double monthlySalary;
        double bonus;
        public FullTimeEmployee(String name, LocalDate started, 
            double monthlySalary, double bonus) {
            super(name, started);
            this.monthlySalary = monthlySalary;
            this.bonus = bonus;
        }
        public double calcSalary() {
            return monthlySalary + bonus;
        }
        public void showInfo() {
            System.out.println("=== Nhân viên Full-Time ===");
            System.out.println("Tên: " + getName());
            System.out.println("Ngày bắt đầu: " + getStarted());
            System.out.printf("Lương cơ bản: %.2f%n", monthlySalary);
            System.out.printf("Thưởng: %.2f%n", bonus);
            System.out.printf("Lương thực nhận: %.2f%n", calcSalary());
            System.out.println();
        }
        //
        }

        class PartTimeEmployee extends Employee {
            //
            int workingHour;
            double rate;
            public PartTimeEmployee(String name, LocalDate started, 
                    int workingHour, double rate) {
                super(name, started);
                this.workingHour = workingHour;
                this.rate = rate;
            }
            public double calcSalary() {
                return workingHour * rate;
            }
            public void showInfo() {
                System.out.println("=== Nhân viên Part-Time ===");
                System.out.println("Tên: " + getName());
                System.out.println("Ngày bắt đầu: " + getStarted());
                System.out.println("Số giờ làm: " + workingHour);
                System.out.printf("Đơn giá/giờ: %.2f%n", rate);
                System.out.printf("Lương thực nhận: %.2f%n", calcSalary());
            }
            //
        }

        //
        FullTimeEmployee ft =
                new FullTimeEmployee(ftName, ftStarted, ftSalary, ftBonus);

        PartTimeEmployee pt =
                new PartTimeEmployee(ptName, ptStarted, ptHour, ptRate);

        ft.showInfo();
        pt.showInfo();
        //

    //C5
        for (int i = 0; i < n; i++) {
            //
            Product p = new Product();
            p.name = sc.next();
            p.category = sc.next();
            p.price = sc.nextDouble();
            p.stock = sc.nextInt();
            list.add(p);
            //
        }
        double minPrice = sc.nextDouble();
        // Stream pipeline
        //
        List<String> result = list.stream()
                .filter(p -> p.stock > 0)
                .filter(p -> p.price >= minPrice)
                .sorted((a, b) -> {
                    if (a.price != b.price) {
                        return Double.compare(b.price, a.price);
                    }
                    return a.name.compareTo(b.name);
                })
                .map(p -> String.format("%s|%s|%.2f",
                        p.name, p.category, p.price))
                .collect(Collectors.toList());

        for (String s : result) {
            System.out.println(s);
        }
        System.out.println("COUNT " + result.size());
        //
//De 3
    //C2
        for(int i =0; i<s.length(); i++){
                char c = s.charAt(i);
                if(tm.containsKey(c)){
                    tm.put(c, tm.get(c)+1);
                }
                else{tm.put(c,1);}
            }
            for(char c : tm.keySet()){
                System.out.println(c + " " + tm.get(c));
            }
    //C5
        // TODO: dùng reduce hoặc max()/min() của IntStream

        int max = IntStream.of(arr).reduce(Integer.MIN_VALUE, Math::max);
        int min = IntStream.of(arr).reduce(Integer.MAX_VALUE, Math::min);
        System.out.println("MAX " + max);
        System.out.println("MIN " + min);
        System.out.println("SUM " + (max + min));
    //C3
        import java.io.*;
        import java.util.*;
        public class Main {
            public static void main(String[] args) throws Exception {
                Scanner sc = new Scanner(System.in);
                String input = sc.nextLine();
                try (BufferedWriter bw = new BufferedWriter(new FileWriter("input.txt"))) {
                    bw.write(input);
                }
                String content = "";
                try (BufferedReader br = new BufferedReader(new FileReader("input.txt"))) {
                    content = br.readLine();
                }
                int letters = 0;
                int digits = 0;
                int others = 0;
                for (int i = 0; i < content.length(); i++) {
                    char c = content.charAt(i);
                    if (Character.isLetter(c)) {
                        letters++;
                    } else if (Character.isDigit(c)) {
                        digits++;
                    } else {
                        others++;
                    }
                }
                System.out.println("Letters: " + letters);
                System.out.println("Digits: " + digits);
                System.out.println("Others: " + others);
            }
        }
    //C1
        import java.util.*;
        import java.time.LocalDate;
        class MyDate {
            int day, month, year;
            MyDate(int d, int m, int y) {
                //
                day = d;
                month = m;
                year = y;
            }
            //
            int compareTo(MyDate o) {
                LocalDate d1 = LocalDate.of(year, month, day);
                LocalDate d2 = LocalDate.of(o.year, o.month, o.day);
                if (d1.isBefore(d2)) return -1;
                if (d1.isAfter(d2)) return 1;
                return 0;
            }
            //
            int daysBetween(MyDate o) {
                LocalDate d1 = LocalDate.of(year, month, day);
                LocalDate d2 = LocalDate.of(o.year, o.month, o.day);
                return (int)Math.abs(d1.toEpochDay() - d2.toEpochDay());
            }
            //
            public String toString() {
                return String.format("%02d/%02d/%04d", day, month, year);
            }
        }
        public class Main {
            public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);
                int q = sc.nextInt();
                // 
                for (int i = 0; i < q; i++) {
                    MyDate d1 = new MyDate(
                            sc.nextInt(),
                            sc.nextInt(),
                            sc.nextInt()
                    );
                    MyDate d2 = new MyDate(
                            sc.nextInt(),
                            sc.nextInt(),
                            sc.nextInt()
                    );
                    String op = sc.next();
                    if (op.equals("CMP")) {
                        int cmp = d1.compareTo(d2);
                        if (cmp < 0)
                            System.out.println("LESS");
                        else if (cmp > 0)
                            System.out.println("GREATER");
                        else
                            System.out.println("EQUAL");
                    }
                    else if (op.equals("DIFF")) {
                        System.out.println(d1.daysBetween(d2));
                    }
                    else if (op.equals("FMT1")) {
                        System.out.println(d1);
                    }
                    else if (op.equals("FMT2")) {
                        System.out.println(d2);
                    }
                }
            }
        }
//De 4
    //C2
        for (int i =0;i<n; i++){
                String key = sc.next();
                int value =sc.nextInt();
                map.put(key,value);
            }
            String keyMax = "";
            int valueMax = -99999;
            for( Map.Entry<String, Integer> e : map.entrySet()){
                String key = e.getKey();
                int value = e.getValue();
                if(value > valueMax){
                    valueMax = value;
                    keyMax = key;
                }
                else if( value == valueMax){
                    if(key.compareTo(keyMax) < 0){
                        keyMax = key;
                    }
                }
            }
            System.out.println(keyMax + " " + valueMax);
    //C5
        // TODO: filter !isEmpty + joining(",")
        String result = list.stream().filter(s -> !s.isEmpty()).collect(Collectors.joining(","));
        System.out.println(result);

    //C1
        class Account {
            String id;
            double balance;
            Account(String id, double balance) {
                this.id = id;
                this.balance = balance;
            }
            void deposit(double amt) {
                // 
                balance += amt;
                //
            }
            double getBalance() {
                return balance;
            }
        }
        class SavingsAccount extends Account {
            double rate;
            SavingsAccount(String id, double balance, double rate) {
                super(id, balance);
                this.rate = rate;
            }
            double balanceAfterYears(int years) {
                //
                return balance * Math.pow(1 + rate, years);
                //
            }
        }

        public class Main {
            public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);
                int n = sc.nextInt();
                // TODO
                HashMap<String, SavingsAccount> map = new HashMap<>();
                for (int i = 0; i < n; i++) {
                    String id = sc.next();
                    double balance = sc.nextDouble();
                    double rate = sc.nextDouble();
                    map.put(id, new SavingsAccount(id, balance, rate));
                }
                int m = sc.nextInt();
                for (int i = 0; i < m; i++) {
                    String command = sc.next();
                    String id = sc.next();
                    SavingsAccount acc = map.get(id);
                    if (command.equals("DEPOSIT")) {
                        double amt = sc.nextDouble();
                        acc.deposit(amt);
                        System.out.printf("%s %.2f\n", id, acc.getBalance());
                    } else if (command.equals("FORECAST")) {
                        int years = sc.nextInt();
                        System.out.printf("%s %.2f\n",id,acc.balanceAfterYears(years));
                    }
                }
                //
            }
        }
    //C4
        // implement
        VarThread(int[] arr, int from, int to) {
        this.arr = arr;
        this.from = from;
        this.to = to;
        }
        @Override
        public void run() {
            for (int i = from; i < to; i++) {
                localSum += arr[i];
                localSumSq += (long) arr[i] * arr[i];
            }
        }

        //int k = sc.nextInt();
        // 
        VarThread[] threads = new VarThread[k];
        for (int i = 0; i < k; i++) {
            int from = i * n / k;
            int to = (i + 1) * n / k;
            threads[i] = new VarThread(arr, from, to);
            threads[i].start();
        }
        long sum = 0;
        long sumSq = 0;
        for (int i = 0; i < k; i++) {
            threads[i].join();
            sum += threads[i].localSum;
            sumSq += threads[i].localSumSq;
        }
        double variance = (double) sumSq / n - Math.pow((double) sum / n, 2);
        System.out.printf("%.4f\n", variance);

//De 5
    //C2
        class Student {
            String name;
            int age;
            double score;
            Student(String name, int age, double score) {
                this.name = name;
                this.age = age;
                this.score = score;
            }
        }
        public class Main {
            public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);
                int N = sc.nextInt();
                ArrayList<Student> list = new ArrayList<>();
                for(int i = 0; i < N; i++) {
                    String name = sc.next();
                    int age = sc.nextInt();
                    double score = sc.nextDouble();
                    list.add(new Student(name, age, score));
                }
                Student best = list.get(0);
                for(Student s : list) {
                    if(s.score > best.score) {
                        best = s;
                    }
                }
                System.out.println("Name: " + best.name);
                System.out.println("Age: " + best.age);
                System.out.printf("Score: %.2f\n", best.score);
            }
        }
    
    //C5
        // TODO: anyMatch / allMatch / noneMatch
        boolean any = list.stream().anyMatch(s -> s >= 9);
        boolean all = list.stream().allMatch(s -> s >= 5);
        boolean none = list.stream().noneMatch(s -> s < 0 || s > 10);
        System.out.println("ANY " + any);
        System.out.println("ALL " + all);
        System.out.println("NONE " + none);
    
    //C3
        // Ghi data.txt
        BufferedWriter bw = new BufferedWriter(new FileWriter("data.txt"));
        while (sc.hasNextLine()) {
            bw.write(sc.nextLine());
            bw.newLine();
        }
        bw.close();
        // Đọc -> List
        ArrayList<String> list = new ArrayList<>();
        BufferedReader br = new BufferedReader(new FileReader("data.txt"));
        String line;
        while ((line = br.readLine()) != null) {
            list.add(line);
        }
        br.close();
        // In ngược
        for (int i = list.size() - 1; i >= 0; i--) {
            System.out.println(list.get(i));
        }   

    //C1
        class Single extends Room {
            Single(String code, int basePrice) {
                this.code = code;
                this.basePrice = basePrice;
            }
            int totalPrice(int nights) {
                return basePrice * nights;
            }
        }
        class Double_ extends Room {
            Double_(String code, int basePrice) {
                this.code = code;
                this.basePrice = basePrice;
            }
            int totalPrice(int nights) {
                return basePrice * nights * 2;
            }
        }
        class Suite extends Room {
            Suite(String code, int basePrice) {
                this.code = code;
                this.basePrice = basePrice;
            }
            int totalPrice(int nights) {
                return basePrice * nights * 3 + 200000;
            }
        }
            
        // TODO
        HashMap<String, Room> map = new HashMap<>();
        for (int i = 0; i < n; i++) {
            String type = sc.next();
            String code = sc.next();
            int basePrice = sc.nextInt();
            if (type.equals("SINGLE")) {
                map.put(code, new Single(code, basePrice));
            } else if (type.equals("DOUBLE")) {
                map.put(code, new Double_(code, basePrice));
            } else {
                map.put(code, new Suite(code, basePrice));
            }
        }
        int m = sc.nextInt();
        long revenue = 0;
        for (int i = 0; i < m; i++) {
            String code = sc.next();
            int nights = sc.nextInt();
            Room room = map.get(code);
            int total = room.totalPrice(nights);
            System.out.println(code + " " + total);
            revenue += total;
        }
        System.out.println("REVENUE " + revenue);
