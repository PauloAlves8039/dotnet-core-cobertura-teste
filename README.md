<h1 align="center">:bar_chart: Dotnet Core Cobertura de Teste</h1>

## :computer: Projeto

Repositório de uma aplicação console para simular o uso de uma simples calculadora, com a realização de testes unitários usando a biblioteca [XUnit](https://xunit.net/) 
e a geraração de um relatório para cobertura de testes.

Para gerar esse relatório com a cobertura de código nesse projeto foi feito o uso de uma biblioteca chamada [Coverlet](https://github.com/coverlet-coverage/coverlet), 
uma ferramenta Cross Plataforma que faz parte do .NET Foundation, onde é feita uma coleta dos dados de execução de teste 
e como resultado é gerado um relatório com essas informações.

Para se obter uma interface gráfica amigável desse relatório é necessário a utilização do [ReportGenerator](https://github.com/danielpalme/ReportGenerator), 
uma ferramenta open source que usa vários formatos legíveis com detalhamento dessas informações.

## :wrench: Recursos Utilizados

- [Visual Studio Code v1.54.2](https://code.visualstudio.com/).
- [.NET Core v5.0.103](https://dotnet.microsoft.com/download/dotnet/5.0).
- [C#](https://code.visualstudio.com/).
- [XUnit v2.4.1](https://xunit.net/).
- [Coverlet v3.0.3](https://github.com/coverlet-coverage/coverlet).
- [ReportGenerator v3.0.3](https://github.com/danielpalme/ReportGenerator).

## :floppy_disk: Clonar repositório

```git clone https://github.com/PauloAlves8039/dotnet-core-cobertura-teste.git```

Ao fazer o clone do projeto basta utilizar o prompt de comando ir ate a pasta ``` src ``` e executar o comando ``` dotnet restore ``` para restaurar os pacotes da aplicação.  

## :arrow_down: Bibliotecas adicionadas

Para a criação de um projeto de teste com XUnit, tem um passo a passo na documentação da [Microsoft](https://docs.microsoft.com/pt-br/dotnet/core/testing/unit-testing-with-dotnet-test).

Foram utilizados os seguintes comandos para adição de pacotes nesse projeto:

Coverlet: ```dotnet add package coverlet.msbuild```
<br/>
ReportGenerator: ```dotnet add package ReportGenerator```

No caso do ReportGenerator também é necessário fazer seu [Download](https://github.com/danielpalme/ReportGenerator/releases) e salvar em um local de fácil acesso,
para que o relatório possa ser gerado.

## :arrow_forward: Gerando a cobertura de código

Executando o seguinte comando, será gerado um arquivo chamado ```coverage.json``` que é o seu formato padrão, 
mas outros formatos também pode ser gerados.  

```dotnet test /p:CollectCoverage=true```

Para alterar o formato do arquivo para opencover que é o desejado para esse projeto, deve ser executado o seguinte comando:

```dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=opencover```

Como resultado é gerado o arquivo ```coverage.opencover.xml``` e um relatório simples no prompt de comando:

![screenshot1](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot1.png)

Com o arquivo no formato opencover gerado pelo Coverlet, um relatório em HTML pode ser gerado, 
para isso abro um novo prompt e navego ate o local onde o ReportGenerator foi salvo e executo o seguinte comando:

```ReportGenerator.exe -reports:-targetdir:\coverage.opencover.xml" -targetdir:./report"```

O targetdir indica o local onde os arquivos do relatório serão gerados, report é a pasta que vai conter os arquivos desse relatório, 
no meu caso o comando que utilizei foi:

```ReportGenerator.exe -reports:"C:\dev\ws-dotnet\dotnet-core-coverlet\src\UsandoCoverlet.Teste\coverage.opencover.xml" -targetdir:"C:\dev\ws-dotnet\dotnet-core-coverlet\src\UsandoCoverlet.Teste\report"```

![screenshot2](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot2.png)

Vou na pasta report onde se encontram os arquivo salvos e clico no ```index.html``` para ser aberta uma página com o relatório:

![screenshot3](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot3.png)

Com esse relatório é posível visualizar as informações sobre a cobertura de código:

![screenshot4](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot4.png)

Para melhorar a cobertura de código desses meus testes, faço as alterações necessárias no projeto de teste e executo novamente o comando:

```dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=opencover```

E como resultado as alterações dos testes são atualizadas:

![screenshot5](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot5.png)

Com outro promt de comando aberto executo novamente o comando:

```ReportGenerator.exe -reports:"C:\dev\ws-dotnet\dotnet-core-coverlet\src\UsandoCoverlet.Teste\coverage.opencover.xml" -targetdir:"C:\dev\ws-dotnet\dotnet-core-coverlet\src\UsandoCoverlet.Teste\report"```

![screenshot2](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot2.png)

E tenho o ```index.html``` com as devidas mudanças na cobertua de código:

![screenshot6](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot6.png)

![screenshot7](https://github.com/PauloAlves8039/dotnet-core-cobertura-teste/blob/master/src/UsandoCoverlet.App/assets/img/screenshot7.png)

Referência:[ Usar cobertura de código para teste de unidade](https://docs.microsoft.com/pt-br/dotnet/core/testing/unit-testing-code-coverage?tabs=windows).

## Author

:boy: [Paulo Alves](https://github.com/PauloAlves8039)

