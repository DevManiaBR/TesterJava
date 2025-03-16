# TesterJava
line for test using JAVA 8 



Passo 1: Instalar Pré-requisitos
Instalar o Java Development Kit (JDK):

Baixe e instale o JDK mais recente no site da Oracle ou OpenJDK.

Verifique a instalação executando os seguintes comandos no terminal:

bash
Copy
java -version
javac -version
Instalar o Visual Studio Code:

Baixe e instale o VS Code em https://code.visualstudio.com/.

Instalar Extensões do Java para o VS Code:

Abra o VS Code e vá para a aba Extensions (Ctrl+Shift+X).

Procure e instale as seguintes extensões:

Extension Pack for Java (da Microsoft): Fornece suporte para a linguagem Java, depuração e ferramentas de teste.

JUnit Test Runner: Permite executar testes JUnit diretamente no VS Code.

Passo 2: Configurar a Estrutura do Projeto
Criar uma Pasta para o Projeto:

Abra um terminal e crie uma nova pasta para o seu projeto:

bash
Copy
mkdir DemoProject
cd DemoProject
Criar as Pastas src e test:

Dentro da pasta DemoProject, crie a seguinte estrutura de diretórios:

Copy
DemoProject/
├── src/
│   └── com/
│       └── exemplo/
│           └── Demo.java
└── test/
    └── com/
        └── exemplo/
            └── DemoTest.java
Você pode criar as pastas e arquivos manualmente ou usar o terminal:

bash
Copy
mkdir -p src/com/exemplo
mkdir -p test/com/exemplo
Abrir o Projeto no VS Code:

Abra a pasta DemoProject no VS Code:

bash
Copy
code .
Passo 3: Criar o Arquivo Demo.java
Criar a Classe Demo:

Na pasta src/com/exemplo/, crie um arquivo chamado Demo.java.

Adicione o seguinte código ao arquivo:

java
Copy
package com.exemplo;

public class Demo {
    public int soma(int a, int b) {
        return a + b;
    }
}
Passo 4: Criar o Arquivo DemoTest.java
Criar a Classe DemoTest:

Na pasta test/com/exemplo/, crie um arquivo chamado DemoTest.java.

Adicione o seguinte código ao arquivo:

java
Copy
package com.exemplo;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class DemoTest {

    @Test
    public void testSoma() {
        Demo demo = new Demo();
        assertEquals(5, demo.soma(2, 3), "2 + 3 deve ser igual a 5");
        assertEquals(-1, demo.soma(-4, 3), "-4 + 3 deve ser igual a -1");
        assertEquals(10, demo.soma(10, 0), "10 + 0 deve ser igual a 10");
        assertEquals(2000000000, demo.soma(1000000000, 1000000000), "1000000000 + 1000000000 deve ser igual a 2000000000");
    }

    @Test
    public void testSomaComNumerosIguais() {
        Demo demo = new Demo();
        assertEquals(8, demo.soma(4, 4), "4 + 4 deve ser igual a 8");
    }

    @Test
    public void testSomaComZeroEZero() {
        Demo demo = new Demo();
        assertEquals(0, demo.soma(0, 0), "0 + 0 deve ser igual a 0");
    }
}
Passo 5: Adicionar Dependência do JUnit
Criar um Arquivo pom.xml (para Maven):

Se você estiver usando o Maven, crie um arquivo pom.xml na raiz do seu projeto (DemoProject/) e adicione o seguinte conteúdo:

xml
Copy
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.exemplo</groupId>
    <artifactId>DemoProject</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-api</artifactId>
            <version>5.10.0</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter-engine</artifactId>
            <version>5.10.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.11.0</version>
                <configuration>
                    <source>17</source>
                    <target>17</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
Run HTML
Compilar o Projeto:

Abra um terminal na pasta DemoProject e execute:

bash
Copy
mvn clean install
Passo 6: Executar os Testes
Executar Testes no VS Code:

Abra o arquivo DemoTest.java no VS Code.

Clique no botão Run Test acima dos métodos @Test ou use a aba Testing na barra lateral para executar todos os testes.

Executar Testes no Terminal:

Se estiver usando o Maven, execute os testes com:

bash
Copy
mvn test
Passo 7: Verificar os Resultados
Se todos os testes passarem, você verá uma marca de verificação verde ou uma mensagem de sucesso no VS Code ou no terminal.

Se algum teste falhar, revise a mensagem de erro e corrija a implementação na classe Demo.

Notas Finais
Se você não estiver usando o Maven, pode adicionar manualmente os arquivos JAR do JUnit ao classpath do seu projeto.

Certifique-se de que as classes Demo e DemoTest estejam nos pacotes corretos (com.exemplo).
