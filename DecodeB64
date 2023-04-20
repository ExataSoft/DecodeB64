/*Algoritmo de decodificação Base64:
  diretamente da base decimal sem usar
  base binária e operador de deslocamento de bits.
  Acesse https://www.onlinegdb.com/online_c_compiler
  para executar testes.
*/
#include <stdio.h> 
#define Max 100 //Comprimento máximo da String. 
//------------------------------------ 
// Base64=[A..Z,a..z,0..9,/,+] 
// Exemplos: BtoD('A') retorna 0 
//           BtoD('Z') retorna 25 
//           BtoD('+') retorna 63 
//------------------------------------ 
int BtoD (char B) 
{  
 if(B>='A'&&B<='Z') return B-'A'; 
 if(B>='a'&&B<='z') return B-'a'+26; 
 if(B>='0'&&B<='9') return B-'0'+52;     
 if(B=='/') return 62; 
 if(B=='+') return 63; 
 if(B=='=') return 64; 
} 
//--------------------------------- 
//Retorna o comprimento da string.
//--------------------------------- 
int len(char *s) 
{ int l=0; 
  for(;*s++;l++);  
  return l;     
} 
//------------------------------ 
// Retorna: 0 Se não for Base64  
//          1 Se for Base64 
//------------------------------ 
int IsBase64(char *sc) 
{ int l=len(sc); 
  if(l%4) return 0; 
  for(int i=0;i<l;i++) 
  { int d=BtoD(sc[i]); 
    if(d<0) return 0; 
    if(d>63&&i<l-2) return 0; 
  }    
  return 1;     
} 
//-------------------------------- 
//Decodifica string em Base64. 
//Suporta somente caracteres  
//imprimíveis. ASCII (32 to 126) 
//-------------------------------- 
void DecodeB64(char *sc, char *sd) 
{ int a,b,c,d,  
  k=0,p=0,t=len(sc),n=t/4; 
  for(int i=0;i<n;i++) 
  {    
    a=BtoD(sc[k++]); b=BtoD(sc[k++]); 
    sd[p++]=a*4+b/16;  
     
    c=BtoD(sc[k++]);  
    if(c!=64) 
    sd[p++]=(b%16)*16+c/4; 
 
    d=BtoD(sc[k++]); 
    if(d!=64) 
      sd[p++]= (c%4)*64+d; 
  }       
  sd[p]='\x0'; 
} 
//---------------------------------------  
//Rotina Principal.
//--------------------------------------- 
int main () 
{ char sc[Max]="QSBhbGVncmlhIGV2aXRhIG1pbCBtYWxlcyBlIHByb2xvbmdhIGEgdmlkYS4="; 
  char sd[Max]; 
  if(IsBase64(sc))  
    { DecodeB64(sc,sd); 
      printf("\n %s \n",sd); 
    }     
  else printf("\n Código Inválido!\n");  
  return 0; 
} 
//---------------------------------------- 
