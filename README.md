using System.Runtime.ExceptionServices;

Console.WriteLine("Pesquisa da Radio");
Console.WriteLine("Por gentileza informe os dados abaixo:");

// definindo variaveis
int idade, homens = 0, mulheres = 0, totalEntrevistados = 0, totalDivorciadasCdl = 0, totalHomensMenor = 0;
int bhfm = 0, fm98 = 0, jovemPan = 0, itatiaia = 0, cdl = 0, outros = 0;
double media = 0, soma = 0;

// Enquanto total de entrevistados for menor <= 10 encerrar a pesquisa, caso contrário, continuar perguntando os dados dos entrevistados
for (int totalPesquisas = 1; totalPesquisas <= 10; totalPesquisas++)
{

    Console.Write("\nInforme a idade: ");
    idade = int.Parse(Console.ReadLine());
    //somando as idades para calcular a media depois
    soma += idade;


    Console.Write("Sexo: \n[M] Masculino \n[F] Feminino\n[M/F]: ");
    string sexo = Console.ReadLine().ToUpper();


    Console.Write("\nEstado Civil: \n[1]Casado\n[2]Solteiro\n[3]Viúvo\n[4]Divorciado: ");
    int estadoCivil = int.Parse(Console.ReadLine());

    Console.Write("\nRadio preferida: \n[1] BHfm \n[2] 98fm \n[3] Jovem Pan \n[4] Itatiaia \n[5] CDL \n[9]Outros: ");
    int radio = int.Parse(Console.ReadLine());

    // Contabilizando as preferências de rádio
    switch (radio)
    {
        case 1: bhfm++; break;
        case 2: fm98++; break;
        case 3: jovemPan++; break;
        case 4: itatiaia++; break;
        case 5: cdl++; break;
        case 9: outros++; break;
        default: Console.WriteLine("Opção Invalida"); break;
    }

    totalEntrevistados++;

    // Exibindo os dados (idade e sexo) informados pelo entrevistado
    if (idade != 0)
    {
        Console.WriteLine($"\nIdade informada: {idade}");
    }

    if (sexo == "M")
    {
        Console.WriteLine("Sexo selecionado: Masculino");
    }
    else if (sexo == "F")
    {
        Console.WriteLine("Sexo selecionado: Feminino");
    }

    // Exibindo o estado civil e a rádio preferida informados pelo entrevistado
    switch (estadoCivil)
    {
        case 1: Console.WriteLine("Estado Civil: Casado"); break;
        case 2: Console.WriteLine("Estado Civil: Solteiro"); break;
        case 3: Console.WriteLine("Estado Civil: Viúvo"); break;
        case 4: Console.WriteLine("Estado Civil: Divorciado"); break;
    }
    switch (radio)
    {
        case 1: Console.WriteLine("Radio preferida: BHfm"); break;
        case 2: Console.WriteLine("Radio preferida: 98fm"); break;
        case 3: Console.WriteLine("Radio preferida: Jovem Pan"); break;
        case 4: Console.WriteLine("Radio preferida: Itatiaia"); break;
        case 5: Console.WriteLine("Radio preferida: CDL"); break;
        case 9: Console.WriteLine("Radio preferida: Outro"); break;
    }

    // b)
    if (sexo == "F" && estadoCivil == 4 && radio == 5)
    {
        totalDivorciadasCdl++;
    }

    //c)
    if (sexo == "M" && idade < 18 && radio == 3)
    {
        totalHomensMenor++;
    }

    // d)
    if (totalEntrevistados != 0)
    {
        media = soma / totalEntrevistados;
    }

    // contabilizando o número de homens e mulheres entrevistados
    if (sexo == "M")
    {
        homens++;
    }
    else if (sexo == "F")
    {
        mulheres++;
    }

}

    Console.WriteLine("\n--- Resultado da Pesquisa ---");
    Console.WriteLine($"Total entrevistados: {totalEntrevistados}\n");
    //A) porcentagem de entrevistados que preferem cada rádio
    if (totalEntrevistados > 0)
    {

        Console.WriteLine($"Bhfm: {(bhfm * 100 / totalEntrevistados):F2}%");
        Console.WriteLine($"98fm: {(fm98 * 100 / totalEntrevistados):F2}%");
        Console.WriteLine($"Jovem Pan: {(jovemPan * 100 / totalEntrevistados):F2}%");
        Console.WriteLine($"Itatiaia: {(itatiaia * 100 / totalEntrevistados):F2}%");
        Console.WriteLine($"CDL: {(cdl * 100 / totalEntrevistados):F2}%");
        Console.WriteLine($"Outros: {(outros * 100 / totalEntrevistados):F2}%");
    }

    //B) total de mulheres divorciadas que preferem CDL
    Console.WriteLine($"\nTotal de mulheres divorciadas que preferem CDL: {totalDivorciadasCdl}");

    //C)nº de homens menores de 18 anos que preferem Jovem Pan
    Console.WriteLine($"\nTotal de homens menores de 18 anos que preferem Jovem Pan: {totalHomensMenor}");

    //D) Media das idades dos entrevistados
    Console.WriteLine($"\nMédia das idades dos entrevistados: {media:F2} anos");

    //E)% de homens e de mulheres
    Console.WriteLine($"\nQuantidade de Homens registrados: {homens}");
    Console.WriteLine($"\nQuantidade de Mulheres registrados: {mulheres}");

    Console.WriteLine("\nEntrevista encerrada!");
    Console.ReadKey();
