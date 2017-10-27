##Buffer overflow
inserire in un file chiamato *pwdcheck.c* il seguente codice:
```
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <stdlib.h>

// Check password
int check(char *pwd) {
  int auth_flag = 0; // flag is false, initially
  char pwd_buffer[16];

  // password is copied into a local buffer
  strcpy(pwd_buffer, pwd);

  if (strcmp(pwd_buffer, "itisme") == 0 )
    auth_flag = 1;

  return auth_flag;
}

int main(int argc, char *argv[]) {
  if (argc < 2){
    printf("Insert a Password!\n");
    exit(1);
}
if (check(argv[1]))
  printf("AUTHENTICATED!\n");
else
  printf("ACCESS DENIED!\n");
}
```
