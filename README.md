# Trabalho-de-IPC-Final
Sistema de cadastro de escola

#include <stdio.h>
#include <stdlib.h>
#include <windows.h>
#include <string.h>
#define TAM 10

void menuPrincipal()
{
    system("cls");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
    printf("§           Menu Principal          §\n");
    printf("§ 1 - Inclusao                      §\n");
    printf("§ 2 - Alteracao                     §\n");
    printf("§ 3 - Consulta                      §\n");
    printf("§ 4 - Exclusao de aluno             §\n");
    printf("§ 5 - Listagens                     §\n");
    printf("§ 0 - Sair do programa              §\n");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
}

void menuConsulta()
{
	system("cls");
	printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
    printf("§           Menu Consulta           §\n");
    printf("§ 1 - Consultar codigo              §\n");
    printf("§ 2 - Voltar                        §\n");
    printf("§ 0 - Sair do programa              §\n");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
		
}
void menuExclusao()
{
	system("cls");
	printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
    printf("§           Menu Exclusao           §\n");
    printf("§ 1 - Aluno                         §\n");
    printf("§ 2 - Voltar                        §\n");
    printf("§ 0 - Sair do programa              §\n");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
		
}

void menuInclusao()
{
    system("cls");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
    printf("§           Menu Inclusao           §\n");
    printf("§ 1 - Aluno                         §\n");
    printf("§ 2 - Voltar                        §\n");
    printf("§ 0 - Sair do programa              §\n");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");

}

void menuAlteracao()
{
	system("cls");
	printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
	printf("§           Menu Alteracao          §\n");
	printf("§ 1 - Nome de aluno                 §\n");
	printf("§ 2 - Data de Nascimento            §\n");
	printf("§ 3 - Nota de provas                §\n");
	printf("§ 4 - voltar                        §\n");
	printf("§ 0 - Sair do programa              §\n");
	printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
}

int leropc ()
{
    int opcao;
    scanf("%d",&opcao);
    return opcao;
}

void menuListagens()
{
    system("cls");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
    printf("§                            Menu Listagens                            §\n");
    printf("§1 - Mostrar todos os alunos cadastrados                               §\n"); 
    printf("§2 - Mostrar alunos a partir de um determinado ano.                    §\n"); 
    printf("§3 - Mostrar alunos que tiveram aprovacao em todas as disciplinas      §\n");
    printf("§4 - Mostrar alunos que tiveram uma ou mais reprovacoes nas disciplinas§\n");
    printf("§5 - Voltar menu                                                       §\n");
    printf("§0 - Sair do programa                                                  §\n");
    printf("§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§§\n");
}
    struct data
	{
    	int dia;
		int mes;
		int ano;
	};
struct cadastroAluno
    {
        int codigo;
        char nome[100];
        struct data dat;
        float notas[5][2];
    };

int main()
{
    struct cadastroAluno cad[TAM];

    int opc;
    int i,j,h,p;
    int contAluno=0;
    int compararANO;
    float media;
    int contMEDIA;
    int quantAluno;
    int acm=0;
    int continuar;
    int alterarNomeCodigo;
    char alterarNome[100];
    int alterarDataCodigo;
    int alterarNotaCodigo;
    int consultaCodigo;
    int codigoExclusao;
    int a;
    
    do
    {
        menuPrincipal();
        {
		

	        opc=leropc();
	        if(opc==4)
			{
				menuExclusao();
				{	
					opc=leropc();
					if(opc==1)
					{
						a=0;
			        	printf("Digite o codigo do aluno que voce quer apagar\n");
			        	scanf("%d",&codigoExclusao);
			        	for(h=0;h<contAluno;h++)
						{
			        		if(cad[h].codigo==codigoExclusao)
							{	a++;
			        			printf("Codigo foi encontrado\n");
								for(j=h;j<contAluno-1;j++)
								{
									cad[j]=cad[j+1];
									
								}	
							}
						}
						if (a>=1){
						
							printf("Aluno excluido com sucesso\n");
							contAluno--;
							acm--;
							system("pause");
						}else{
							printf("Codigo nao cadrastrado\n");
							system ("pause");
						}
					}
					else if(opc==2)
					{
						;	
					}
				}
			}
	        
	        else if(opc==3) //ACESSANDO A OPÇAO 3 DO MENU PRINCIPAL
			{
				menuConsulta();
				{
					opc=leropc();
					
					if(opc==1)//ACESSANDO A POÇAO 1 DO MENU CONSULTA
					{
						printf("Voce deseja consultar qual codigo?\n");
						scanf("%d",&consultaCodigo);
						for(h=0;h<contAluno;h++)
						{
							if(cad[h].codigo==consultaCodigo)
							{	
								printf("Codigo encontrado\n");
								printf("%d",cad[h].codigo);
		                        printf(" %s",cad[h].nome);
		                        printf(" %d / %d / %d \n",cad[h].dat.dia, cad[h].dat.mes, cad[h].dat.ano);
		                        for(j=0; j<5; j++)
		                        {
		                            for (i=0; i<2; i++)
		                            {
		                                printf("%.1f ",cad[h].notas[j][i]);
		                            }
		                            printf("\n");
		                        }
									
							}	
						}
						system("pause");
					}
					else if(opc==2)
					{
						
					}
				}	
			}
	        
	        else if(opc==2)   //ACESSANDO MENU DE ALTERAÇÃO
			{
				menuAlteracao();
				{
					opc=leropc();
					
					if(opc==1) //ACESSANDO OPÇÃO 1 DO MENU DE ALTERAÇÃO
					{
						printf("Deseja alterar o nome de qual aluno\n");
						printf("Digite o codigo do aluno no qual a data vai ser alterado:\n");
						scanf("%d",&alterarNomeCodigo);
						for(h=0;h<contAluno;h++)
	                    {
	                        if(cad[h].codigo==alterarNomeCodigo)
	                        {
	                            printf("Digite o novo nome para o aluno %d %s:\n",cad[h].codigo,cad[h].nome);
	                            scanf("%s",alterarNome);
	                            strcpy(cad[h].nome,alterarNome);
	                            printf("O nome do aluno foi alterado para %s\n",cad[h].nome);
								system("pause");
	                        }

	                    }
					}
					else if(opc==2)//ACESSANDO OPÇÃO 2 DO MENU DE ALTERAÇÃO
					{
						printf("Deseja alterar a data de nascimento de qual aluno\n");
						printf("Digite o codigo do aluno a ser alterado:\n");
						scanf("%d",&alterarDataCodigo);
						for(h=0;h<contAluno;h++)
						{
							if(cad[h].codigo==alterarDataCodigo)
							{
								printf("Digite a nova data para o aluno %d %s\n",cad[h].codigo,cad[h].nome);
		                   		printf("digite o dia do aniversario\n");
		                    	scanf("%d",&cad[h].dat.dia);
		                    	printf("digite o mes\n");
		                    	scanf("%d",&cad[h].dat.mes);
		                    	printf("digite o ano\n");
		                    	scanf("%d",&cad[h].dat.ano);
		                    	printf("A data do aluno foi alterada para %d / %d / %d \n",cad[h].dat.dia,cad[h].dat.mes,cad[h].dat.ano);
		                    	system("pause");
							}
						}
					}
					else if(opc==3)//ACESSANDO OPÇÃO 3 DO MENU DE ALTERAÇÃO
					{
						printf("Deseja alterar a nota de qual aluno?\n");
						printf("Digite o codigo do aluno a ser alterado:\n");
						scanf("%d",&alterarNotaCodigo);
						for(h=0;h<contAluno;h++)
						{
							if(cad[h].codigo==alterarNotaCodigo)
							{
								printf("Digite a nova nota para o aluno %d %s\n",cad[h].codigo,cad[h].nome);
								printf("Digite o numero da materia que vc deseja alterar (1,2,3,4,5)\n");
								scanf("%d",&j);
								if (j<1 || j>5)
								{
									do
									{
										printf("Nao existe essa materia\n");
										printf("Digite o numero da materia que vc deseja alterar(1,2,3,4,5,)\n");
										scanf("%d",&j);
										
									}while(j<1 || j>5);
									
								}
								
			                    for (i=0; i<2; i++)
			                    {
			                    	printf("digite a nota da %d prova da %d materia: \n",i+1,j);
			                    	scanf("%f",&cad[h].notas[j-1][i]);
			                    }
			                    printf("A nota do aluno %d %s na materia %d foi alterada para:%.1f %.1f\n",cad[h].codigo,cad[h].nome,j,cad[h].notas[j-1][0],cad[h].notas[j-1][1]);
			                    system("pause");
							}
						}
					}
					else if(opc==4)//ACESSANDO OPÇÃO 4 DO MENU DE ALTERAÇÃO VOLTANDO MENU
					{
						
					}
					
				}
			}
	
	        //MENU LISTAGENS
	
	        else if(opc==5) // ACESSANDO A OPCAO 5 DO MENU E INDO PARA LISTAGENS
	        {
	            menuListagens();
	            {
	                opc=leropc();
	
	                if(opc==1) // ACESSANDO A OPçAO 1 DO MENU LISTAGENS
	                {
	                    for(h=0; h<contAluno; h++)
	                    {	
							
				
	                        printf("%d",cad[h].codigo);
	                        printf(" %s",cad[h].nome);
	                        printf(" %d / %d / %d \n",cad[h].dat.dia, cad[h].dat.mes, cad[h].dat.ano);
							
	                  		for(j=0; j<5; j++)
	                        {
	                            for (i=0; i<2; i++)
	                            {
	                                printf("%.1f ",cad[h].notas[j][i]);
	
	                            }
	                            printf("\n");
	                        }
							
	                    }
	                    system("pause");
	                }
	                else if (opc==2)  //ACESSANDO A OPCAO 2 DO MENU LISTAGENS
	                {
	                    printf("Mostrar alunos a partir de um ano \n digite o ano desejado:\n");
	
	                    scanf("%d",&compararANO);
	
	                    for(h=0;h<contAluno;h++)
	                    {	
	                        if(cad[h].dat.ano>=compararANO)
	                        {
	                            printf("%d",cad[h].codigo);
	                            printf(" %s",cad[h].nome);
	                            printf(" %d / %d / %d \n",cad[h].dat.dia, cad[h].dat.mes, cad[h].dat.ano);
	
	                            for(j=0; j<5; j++)
	                            {
	                                for (i=0; i<2; i++)
	                                {
	                                    printf("%.1f ",cad[h].notas[j][i]);
	
	                                }
	                                printf("\n");
	                            }
	
	                        }
	                    	
	                    }
	                    system("pause");
	                }
	                else if(opc==3) //ACESSANDO A OPÇÃO 3 DO MENU LISTAGENS
	                {
	                	//media=0;
	                	
	                	
	                    for(h=0;h<contAluno;h++)
	                    {	
                    		contMEDIA=0;
	                        for(j=0; j<5; j++)
	                        {	media=0;
	                        	
                				
	                            media=(cad[h].notas[j][0]+cad[h].notas[j][1])/2;
	                            if(media >= 6)
	                            {
	                                contMEDIA++;
	                                if(contMEDIA == 5)
	                                {
	                                    //PRINTAR O ALUNO QUE PASSOU EM TUDO
	                                    printf("%d",cad[h].codigo);
	                                    printf(" %s",cad[h].nome);
	                                    printf(" %d / %d / %d \n",cad[h].dat.dia, cad[h].dat.mes, cad[h].dat.ano);
	
	                                    for(j=0; j<5; j++)
	                                    {
	                                        for (i=0; i<2; i++)
	                                        {
	                                            //printf("%f ",cad[h].notas[j][i]);
	
	                                        }
	                                        printf("\n media da %d materia : %.1f ",j+1,media=(cad[h].notas[j][0]+cad[h].notas[j][1])/2);
	                                    }
										printf("\n");
	                                } 
	                            }
	                        }
	                        printf("\n");
							
	                    }
						printf("\n");
						system("pause");
	                }
	                else if(opc==4) //ACESSANDO A OPÇÃO 4 DO MENU LISTAGENS
	                {
	                	media=0;
	                	contMEDIA=0;
	                	
	                    for(h=0;h<contAluno;h++)
	                    {	
	                        for(j=0; j<5; j++)
	                        {
	                            media=(cad[h].notas[j][0]+cad[h].notas[j][1])/2;
	                            if(media < 6)
	                            {
	                                contMEDIA++;
	                                if(contMEDIA < 5)
	                                {
	                                    //PRINTAR OS ALUNOS QUE TIVERAM 1 OU MAIS REPROVAçõES
	
	                                    printf("%d",cad[h].codigo);
	                                    printf(" %s",cad[h].nome);
	                                    printf(" %d / %d / %d \n",cad[h].dat.dia, cad[h].dat.mes, cad[h].dat.ano);
	
	                                    for(j=0; j<5; j++)
	                                    {
	                                        for (i=0; i<2; i++)
	                                        {
	
	                                        }
	                                        printf("\n media da %d materia : %.1f ",j+1,media=(cad[h].notas[j][0]+cad[h].notas[j][1])/2);
	                                        printf("\n");
	                                    }
	                                }
	                            }
	                        }
	                    	
	                    }
	                    if(contMEDIA==0)
						{
	                    	printf("Nenhum aluno encontrado\n");
						}
	                    system("pause");
	                }
	                else if(opc==5) // ACESSANDO A OPCAO 5 DO MENU LISTAGENS E VOLTANDO PARA O MENU
	                {
	                   // menuPrincipal();
	                }
	            }
	        }
	
	        //FIM MENU LISTAGENS
	
	
	        //MENU INCLUSÃO
	        else if (opc==1)  // ACESSANDO A OPCAO 1 DO MENU E INDO PARA O MENU DE INCLUSAO
	        {
	            menuInclusao();
	            {
	                opc=leropc();
	                if (opc==1) // ACESSANDO A OPCAO 1 DO MENU INCLUSAO
	                {
						do
						{
		                    
			            	if(contAluno>=TAM)
							{
				               	printf("numero de alunos excedidos ");
				                Sleep(1700);
				                break;
				            }
		
		                    printf("digite o codigo do aluno %d\n",acm+1);
		                    scanf("%d",&cad[acm].codigo);
		                    int contCodigo=0;
		                    do
							{
		                    	contCodigo=0;
		                        for(p=0;p<acm;p++)
								{
		                        	if(cad[acm].codigo==cad[p].codigo)
									{
		                                printf("\nCodigo esta repetido digite um novo codigo\n");
		                                scanf("%d",&cad[acm].codigo);
		                                contCodigo++;
		                            }
		                        }
		                    }while(contCodigo !=0);
							
		                    printf("digite o nome\n");
		                    setbuf(stdin,NULL);
		                    gets(cad[acm].nome);
		                    printf("Digite a data de nascimento\n");
		                    printf("digite o dia do aniversario\n");
		                    scanf("%d",&cad[acm].dat.dia);
		                    printf("digite o mes\n");
		                    scanf("%d",&cad[acm].dat.mes);
		                    printf("digite o ano\n");
		                    scanf("%d",&cad[acm].dat.ano);
		
		                    printf("digite a nota do aluno %d \n",acm+1);
		                    for(j=0; j<5; j++)
		                    {
		                        for (i=0; i<2; i++)
		                        {
		                            printf("digite a nota da %d prova da %d materia: \n",i+1,j+1);
		                            scanf("%f",&cad[acm].notas[j][i]);
		                        }
		                    }
		                    contAluno++;
		                    acm++;
		                	printf("Aperte qualquer numero diferente de 0 para continuar \n0-Sair\n");
		                	scanf("%d",&continuar);
		                	system("pause");
	                    }while(continuar!= 0);
	                }else if(opc==2) // ACESSANDO A OPCAO 2 DO MENU INCLUSAO E VOLTANDO NO MENU PRINCIPAL
	                {
	                    ;// menuPrincipal()
	                }
	            }
	        }
	
	        //FIM MENU INCLUSÃO
		}

    }while(opc!=0);



    return 0;
}
