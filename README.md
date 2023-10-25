# Repetição

Exercícios presentes no link:

> https://darlonv.github.io/algoritmos/docs/Controle/Exercicios/Repeticao


### 1) Peça ao usuário que digite um valor inteiro n. Mostre na tela os números de 1 até n, em sequência.

~~~
public static void main(String[] args) {
    Scanner entrada = new Scanner(System.in);

    System.out.println("Digite um numero: ");
    int n = entrada.nextInt();
    
    entrada.close();
    int i = 0;
    while ( i <= n){
        System.out.println(i);
        i++;
    }
}
~~~

### 2) Peça o usuário que digite 5 números, com valores que podem ser entre 0 e 1000. Mostre o maior e menor número digitados.

~~~
public static void main(String[] args) {
        Scanner entrada = new Scanner(System.in);
        
        int n = 0, 
        maior = 1000,
        menor = 0;

        System.out.println("Digite 5 numeros: ");         
        int i = 0;
        while (i < 5){            
            n = entrada.nextInt();
            
            if (n <= 1000 && n >= 0){                  
                
                if (n >= menor){
                    menor = n;                
                }               
                if (n <= maior){
                    maior = n;                
                }
                                
            }
              
            i++;
        }

        System.out.printf("Menor numero e: %d e o maior numero e: %d ",maior, menor);        
        
        entrada.close();
}
~~~

### 3) Peça ao usuário que digite um valor inteiro n. Em seguida, apresente os números de n a 1, na ordem do maior para o menor.

~~~
public static void main(String[] args) {
        Scanner entrada = new Scanner(System.in);
        int n;

        System.out.println("Digite um valor: ");
        n = entrada.nextInt();
        entrada.close();

        int i = 0;
        while ( i < n){
            System.out.println(n);
            n--;
        }
}
~~~

### 4) Pergunte um número k ao usuário, e mostre a tabuada desse número, com múltiplos de 1 a 20.

~~~
public static void main(String[] args) {
    Scanner entrada = new Scanner(System.in);
    int k , i = 0, resultado;

    System.out.println("Digite um valor para obter sua tabuada: ");
    k = entrada.nextInt();    
    entrada.close();
    
    System.out.printf("A tabuada de %d até os multiplos de 20 é: \n",k);

    while (i <= 20){

        resultado = k * i;
        
        System.out.printf( "%d x %d = %d \n",k, i, resultado);
        i++;
    }    
}
~~~

### 5) Calcule a soma s e a média m dos primeiros n números, começando por 1, de forma que n é digitado pelo usuário.

~~~
public static void main(String[] args) {
    Scanner entrada = new Scanner(System.in);    
    int s, n, i;
    float m;
    
    System.out.println("Digite um valor: ");
    n = entrada.nextInt();
    entrada.close();

    for (i = 1; i < n; i++) {

        s = n + i;
        m = s/n;

        System.out.printf("A soma e: %d e a media e: %.2f \n", s, m);
    }

}
~~~

