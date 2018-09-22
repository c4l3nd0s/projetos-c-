# projetos-c-
meus projetos acadêmicos enquanto sou iniciante, aberto a correções 
//projeto de um calendario de um mes especifico, de qualquer ano...


#include <stdio.h>
int calcDiaSemana(int mes, int ano);
int diasMeses(int meses, int ano);
void imprimirCalendario(int mes, int ano, int calcDiaSemana(int mes, int ano), int diasMeses( int mes, int ano));
int main()
{
    int mes;
    int ano;
    
    printf("Digite o mes desejado na forma 1-12:\n");
    scanf("%d" ,&mes);
    
    while(mes<1 || mes>12) //consistencia de dados
    { 
        printf("Mes inválido, digite um mes na forma 1-12:\n");
        scanf("%d" ,&mes);
    }
    
    printf("Digite o ano desejado:\n");
    scanf("%d" ,&ano);
    
    imprimirCalendario(mes,ano, calcDiaSemana, diasMeses);
    
    
    return 0;
}
int diasMeses(int mes, int ano)
{   
    int mestem=0;
    if(mes==1 || mes==3 || mes==5 || mes==7 || mes==8 || mes==10 || mes==12)
        mestem=31;
    else if(mes==4 || mes==6 || mes==9 || mes==11)
        mestem=30;
    else if(mes==2 && ano % 4 == 0 && (ano % 400 == 0 || ano % 100 != 0))
        mestem=29;
    else
        mestem=28;
    
    return mestem;
}
int calcDiaSemana(int mes, int ano){
    /*calculo do dia da semana. Foi divididos em processos nomeados de 1 a 5,
    como o calculo usa apenas o mes e o ano, o dia inicial sempre sera o primeiro dia de cada mes,
    facilitando assim a impressao do calendario*/
    
    int dia=1; //dia inicial fixo
    int proc1; 
    int proc2;
    int proc3;
    int proc4;
    int proc5;  
    int diaDaSem; //dia da semana como um numero. ex: 1-dom,2-seg...7-sabado
    
    proc1=(14-mes)/12; //calculo do dia da semana
    proc2=ano-proc1;
    proc3=mes+12*proc1-2;
    proc4=dia + (31*proc3)/12+proc2+proc2/4-proc2/100+proc2/400;
    proc5=proc4%7 +1; //fim do calculo dia da semana
    
    diaDaSem=proc5; 
    
    return diaDaSem; //o retorno eh um dia da semana como um numero. ex: 1-dom,2-seg...7-sabado
}
void imprimirCalendario(int mes, int ano, int calcDiaSemana(int mes, int ano), int diasMeses (int mes, int ano))
{   
    int i;
    int j;
    int esp;// variavel de espaços
    
    if(mes==1)
        printf("\tJaneiro de %d.\n", ano);
        
    if(mes==2)
        printf("\tFevereiro de %d.\n", ano);
        
    if(mes==3)
        printf("\tMarço de %d.\n", ano);
        
    if(mes==4)
        printf("\tAbril de %d.\n", ano);
        
    if(mes==5)
        printf("\tMaio de %d.\n", ano);
        
    if(mes==6)
        printf("\tJunho de %d.\n", ano);
        
    if(mes==7)
        printf("\tJulho de %d.\n", ano);
        
    if(mes==8)
        printf("\tAgosto de %d.\n", ano);
        
    if(mes==9)
        printf("\tSetembro de %d.\n", ano);
        
    if(mes==10)
        printf("\tOutubro de %d.\n", ano);
        
    if(mes==11)
       printf("\tNovembro de %d.\n", ano);
       
    if(mes==12)
        printf("\tDezembro de %d.\n", ano);
        
    printf("DOM  SEG  TER  QUA  QUI  SEX  SAB\n");
    for(esp=1; esp<calcDiaSemana(mes, ano); esp++)
    {
        printf("     "); //qtd de espaços 
        j++; // o contador da semana comeca contando os espaços
    }
    for (i=1; i<=diasMeses(mes, ano); i++)
    {
        printf("%3d  ", i);//impressao dos dias referentes ao mes escolhido
        j++;
        
    if (j==7)
    {
        printf("\n"); // quebra de linha a cada 7 dias
        j=0;
    }
    }
}
