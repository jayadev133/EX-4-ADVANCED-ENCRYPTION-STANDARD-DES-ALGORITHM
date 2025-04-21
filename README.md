## AES Encryption and decryption  

## Aim:-  
To implement a C program that takes the user's name as input and performs simple encryption 
and decryption using a key-based XOR algorithm.  

## Algorithm:  
1. Start the program.  
2. Declare arrays for input, key, encrypted data, and decrypted data.  
3. Get user input (e.g., name) and store it in the input array.  
4. Remove the newline character from the input if present.  
5. Encrypt the input by XOR in each character with the key and store it.  
6. Display the encrypted output in hexadecimal format.  
7. Decrypt the encrypted data using XOR with the same key.  
8. Display the decrypted output (original name).  
9. End the program.  

## Program code:  
#include <stdio.h>  
#include <stdint.h>  
#include <string.h>  
void encrypt(uint8_t *data, uint8_t *key, uint8_t *output, int len) {  
for (int i = 0; i < len; i++) {  
output[i] = data[i] ^ key[i % 16]; // key repeated  
}  
}  
void decrypt(uint8_t *data, uint8_t *key, uint8_t *output, int len) {  
for (int i = 0; i < len; i++) {  
output[i] = data[i] ^ key[i % 16];  
    }  
}  
  
int main() {  
    uint8_t key[16] = "simpleaeskey1234";  
    uint8_t input[MAX_LEN], encrypted[MAX_LEN], decrypted[MAX_LEN];  
  
    printf("Enter your name: ");  
    fgets((char*)input, MAX_LEN, stdin);  
    int len = strlen((char*)input);  
  
    if (input[len - 1] == '\n') {  
        input[len - 1] = '\0'; // remove newline  
        len--;  
    }  
  
    encrypt(input, key, encrypted, len);  
  
    printf("Encrypted: ");  
    for (int i = 0; i < len; i++) {  
        printf("%02x ", encrypted[i]);  
    }  
    printf("\n");  
  
    decrypt(encrypted, key, decrypted, len);  
    decrypted[len] = '\0'; // Null-terminate string  
  
    printf("Decrypted: %s\n", decrypted);  
  
    return 0;  
}   

## Output:  
![Screenshot 2025-04-21 153941](https://github.com/user-attachments/assets/7ab52258-3ffa-4ab7-a3d2-e48718443e66)

## Result:   
The program successfully encrypted and decrypted the user's name using the XOR algorithm.
