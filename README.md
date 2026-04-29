# HILL CIPHER
HILL CIPHER

## PROGRAM 
```
#include <stdio.h> 
#include <string.h> 
#include <ctype.h> 
int keymat[3][3] = { 
{ 17, 17, 5 }, 
{ 21, 18, 21 }, 
{ 2, 2, 19 } 
}; 
int invkeymat[3][3] = { 
{ 4, 9, 15 }, 
{ 15, 17, 6 }, 
{ 24, 0, 17 } 
}; 
char key[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"; 
void encode(char *ret, char a, char b, char c) { 
int x, y, z; 
int posa = (int)a - 65; 
int posb = (int)b - 65; 
int posc = (int)c - 65; 
x = posa * keymat[0][0] + posb * keymat[1][0] + posc * keymat[2][0]; 
y = posa * keymat[0][1] + posb * keymat[1][1] + posc * keymat[2][1]; 
z = posa * keymat[0][2] + posb * keymat[1][2] + posc * keymat[2][2]; 
ret[0] = key[x % 26]; 
ret[1] = key[y % 26]; 
ret[2] = key[z % 26]; 
ret[3] = '\0'; 
} 
void decode(char *ret, char a, char b, char c) { 
int x, y, z; 
int posa = (int)a - 65; 
int posb = (int)b - 65; 
int posc = (int)c - 65; 
x = posa * invkeymat[0][0] + posb * invkeymat[1][0] + posc * invkeymat[2][0]; 
y = posa * invkeymat[0][1] + posb * invkeymat[1][1] + posc * invkeymat[2][1]; 
z = posa * invkeymat[0][2] + posb * invkeymat[1][2] + posc * invkeymat[2][2]; 
ret[0] = key[(x % 26 < 0) ? (26 + x % 26) : (x % 26)]; 
ret[1] = key[(y % 26 < 0) ? (26 + y % 26) : (y % 26)]; 
ret[2] = key[(z % 26 < 0) ? (26 + z % 26) : (z % 26)]; 
ret[3] = '\0'; 
} 
 
int main() { 
    char msg[1000]; 
    char enc[1000] = ""; 
    char dec[1000] = ""; 
    int n; 
     
    printf("enter text:"); 
    scanf("%s",msg); 
    printf("Simulation of Hill Cipher\n"); 
     
     
    for (int i = 0; i < strlen(msg); i++) { 
        msg[i] = toupper(msg[i]); 
    } 
     
    n = strlen(msg) % 3; 
    if (n != 0) { 
        for (int i = 1; i <= (3 - n); i++) { 
            strcat(msg, "X"); 
        } 
    } 
     
    printf("Padded message : %s\n", msg); 
     
    for (int i = 0; i < strlen(msg); i += 3) { 
char temp[4]; 
encode(temp, msg[i], msg[i + 1], msg[i + 2]); 
strcat(enc, temp); 
} 
printf("Encoded message : %s\n", enc); 
for (int i = 0; i < strlen(enc); i += 3) { 
char temp[4]; 
decode(temp, enc[i], enc[i + 1], enc[i + 2]); 
strcat(dec, temp); 
} 
printf("Decoded message : %s\n", dec); 
return 0; 
}
```
## OUTPUT

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1adec764-2559-411c-8218-219f573196b0" />


