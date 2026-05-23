
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

    
