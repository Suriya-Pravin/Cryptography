### Date: 17.10.2024 
# Ex-14: Hash
## AIM:
To implement a simple hash generation and verification process using a custom hash function based on XOR and addition.

## ALGORITHM:

### STEP 1:
Input a message from the user.

### STEP 2:
Use a basic custom hash function that applies XOR and addition on each character of the message.

### STEP 3:
Convert the resulting hash into a hexadecimal format.

### STEP 5:
Verify the hash by comparing it with a received hash entered by the user.
## Program:
```
#include <stdio.h>
#include <string.h>

unsigned char compute_simple_hash(const char *message) {
    int temp = 0;

    for (int i = 0; i < strlen(message); i++) {
        temp = temp ^ message[i];  
        temp += message[i];        
    }

    return temp & 0xFF; 
}

int main() {
    char message[256];
    char received_hash_hex[3];
    unsigned char hash_value, received_hash_value;

    printf("Enter the message: ");
    fgets(message, sizeof(message), stdin);
    message[strcspn(message, "\n")] = 0;  

    hash_value = compute_simple_hash(message);

    printf("Computed Hash (in hex): %02x\n", hash_value);

    printf("Enter the received hash (in hex): ");
    fgets(received_hash_hex, sizeof(received_hash_hex), stdin);
    received_hash_hex[strcspn(received_hash_hex, "\n")] = 0;  // Remove trailing newline

    sscanf(received_hash_hex, "%2hhx", &received_hash_value);

    if (hash_value == received_hash_value) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}

```
## Output:
![14](https://github.com/user-attachments/assets/61b52e40-a5b9-4d1b-ad9d-8a3e85a75356)


## Result:
The program for generating and verifying a simple hash using a custom hash function was successfully implemented and executed. The computed hash ensures basic message integrity and was successfully verified against the received hash.
