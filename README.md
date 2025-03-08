# Manipulação de Strings e Arrays em Java

## **Manipulação de Strings**

### **1. Imutabilidade da `String`**
Em Java, `String` é **imutável**, ou seja, qualquer alteração cria um novo objeto na memória.

```java
String nome = "Java";
nome.concat(" é incrível!"); 
System.out.println(nome); // "Java" (o original não muda)
```

Para manipulações eficientes, use `StringBuilder` ou `StringBuffer`.

---

### **2. Métodos Principais da Classe `String`**
```java
String texto = "Java Backend";

// Tamanho da string
System.out.println(texto.length()); // 13

// Maiúsculas e minúsculas
System.out.println(texto.toUpperCase()); // "JAVA BACKEND"
System.out.println(texto.toLowerCase()); // "java backend"

// Comparação (case-sensitive e ignorando maiúsculas/minúsculas)
System.out.println(texto.equals("java backend")); // false
System.out.println(texto.equalsIgnoreCase("java backend")); // true

// Verificação de início e fim
System.out.println(texto.startsWith("Java")); // true
System.out.println(texto.endsWith("end")); // true

// Substring (parte da string)
System.out.println(texto.substring(5)); // "Backend"
System.out.println(texto.substring(0, 4)); // "Java"

// Substituição de caracteres/palavras
System.out.println(texto.replace("Backend", "Developer")); // "Java Developer"

// Remoção de espaços extras
String sujo = "   Java   ";
System.out.println(sujo.trim()); // "Java"

// Quebrar string em array
String[] palavras = texto.split(" "); // ["Java", "Backend"]
System.out.println(palavras[1]); // "Backend"
```

---

### **3. Uso de `StringBuilder` e `StringBuffer`**
Se precisar **modificar strings frequentemente**, use `StringBuilder` (não sincronizado, mais rápido) ou `StringBuffer` (sincronizado, seguro para múltiplas threads).

```java
StringBuilder sb = new StringBuilder("Java");
sb.append(" Backend");
System.out.println(sb.toString()); // "Java Backend"
sb.reverse();
System.out.println(sb.toString()); // "dnekcab avaJ"
```

---

## **Manipulação de Arrays**

### **1. Declaração e Inicialização**
```java
// Declarando e inicializando
int[] numeros = {10, 20, 30, 40};
String[] nomes = new String[3]; // ["null", "null", "null"]
nomes[0] = "Ana";
```

---

### **2. Acessando e Modificando Elementos**
```java
System.out.println(numeros[1]); // 20
numeros[2] = 100;
System.out.println(numeros[2]); // 100
```

---

### **3. Iterando sobre Arrays**
```java
int[] valores = {5, 10, 15, 20};

// Usando for clássico
for (int i = 0; i < valores.length; i++) {
    System.out.println(valores[i]);
}

// Usando for-each
for (int v : valores) {
    System.out.println(v);
}
```

---

### **4. Métodos Úteis da Classe `Arrays`**
A classe `Arrays` do pacote `java.util` oferece métodos úteis para manipulação de arrays.

```java
import java.util.Arrays;

int[] numeros = {3, 1, 4, 1, 5, 9};

// Ordenar array
Arrays.sort(numeros);
System.out.println(Arrays.toString(numeros)); // [1, 1, 3, 4, 5, 9]

// Buscar um elemento (precisa estar ordenado)
int index = Arrays.binarySearch(numeros, 4);
System.out.println(index); // 2 (posição no array)

// Preencher array com um valor padrão
Arrays.fill(numeros, 7);
System.out.println(Arrays.toString(numeros)); // [7, 7, 7, 7, 7, 7]

// Comparar arrays
int[] a = {1, 2, 3};
int[] b = {1, 2, 3};
System.out.println(Arrays.equals(a, b)); // true
```

---

### **5. Convertendo Arrays para Lista**
```java
import java.util.Arrays;
import java.util.List;

String[] frutas = {"Maçã", "Banana", "Uva"};
List<String> lista = Arrays.asList(frutas);
System.out.println(lista); // [Maçã, Banana, Uva]
```

---

### **6. Trabalhando com `Stream API` (Java 8+)**
Para manipular arrays de forma funcional:

```java
import java.util.Arrays;
import java.util.stream.IntStream;

int[] numeros = {1, 2, 3, 4, 5};

// Somar todos os elementos
int soma = Arrays.stream(numeros).sum();
System.out.println(soma); // 15

// Filtrar números pares
int[] pares = Arrays.stream(numeros)
                    .filter(n -> n % 2 == 0)
                    .toArray();
System.out.println(Arrays.toString(pares)); // [2, 4]
```

---

## **Resumo**
- **Strings são imutáveis**, então para modificações constantes use `StringBuilder`.  
- **Métodos úteis da `String`** → `substring()`, `replace()`, `split()`, `trim()`, `toUpperCase()`.  
- **Arrays são estáticos** → Prefira `ArrayList` para mais flexibilidade.  
- **Classe `Arrays`** → Métodos como `sort()`, `fill()`, `binarySearch()`, `equals()`.  
- **Stream API** → Permite manipulação funcional de arrays.
