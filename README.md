# VSD-Internship

<details>
  <summary>Task1</summary>

```
cd
```

```

leafpad sum1ton.c
```

```
gcc sum1ton.c
```

```
ls -ltr
```

```
./a.out
```




![Screenshot 2024-11-22 201754](https://github.com/user-attachments/assets/224cad40-c7fb-40df-aee4-d17bc776d46b)


![Screenshot 2024-11-23 223821](https://github.com/user-attachments/assets/d6869ce0-8842-4633-aca5-47b1c9f01600)


```
cat sum1ton.c
```



![Screenshot 2024-11-26 155243](https://github.com/user-attachments/assets/2b2e6120-1ec6-42ea-966d-728c444cda2a)

```
riscv64-unknown-elf-gcc -O1 mabi=lp64 -march=rv64i -osum1ton.c sum1ton.c
```

![Screenshot 2024-11-26 154713](https://github.com/user-attachments/assets/e621cdf4-0a80-4e5d-a9fe-f14c7a49dd5a)


![Screenshot 2024-11-26 155157](https://github.com/user-attachments/assets/ce03a69e-5bbc-48ba-8a9c-0c8cebba9ac1)
</details>

<details>
 <summary>Task2</summary>

```
riscv64-unknown-elf-gcc -O1 mabi=lp64 -march=rv64i -osum1ton.c sum1ton.c
```

```
gcc sum1ton.c
```

```
./a.out
```

```
riscv64-unknown-elf-gcc -O1 mabi=lp64 -march=rv64i -osum1ton.c sum1ton.c
```

```
spike pk sum1ton.o
```

 ![Screenshot 2024-11-26 163523](https://github.com/user-attachments/assets/9b1b99c2-67ea-481f-893a-ffc941de284e)
 ![Screenshot 2024-11-26 163847](https://github.com/user-attachments/assets/bf677c63-bd2a-4fa8-9c92-fba81dc1e314)
![Screenshot 2024-11-28 002509](https://github.com/user-attachments/assets/10583888-cbdb-41ba-8453-182ffc0c8f81)
![Screenshot 2024-11-28 004621](https://github.com/user-attachments/assets/b89cc490-ef27-42dd-82eb-94a115eb8a92)
![Screenshot 2024-11-28 005212](https://github.com/user-attachments/assets/3ac04ab4-e2ee-4d58-8e6a-ed56fe0cdffa)

</details>






