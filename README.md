# Ex--14---Hash

## AIM:
To generate a simple hash of a given message using a custom hash function.

## DESIGN STEPS:
### STEP 1:
Input a message from the user.

### STEP 2:
Use a basic custom hash function that applies simple operations like XOR and addition on the characters of the message.

### STEP 3:
Convert the resulting hash into a hexadecimal format.

### STEP 4:
Display the computed hash to the user.

### STEP 5:
Optionally verify the hash by recomputing it and comparing it with a received hash.

## PROGRAM:
~~~
#include <stdio.h>
#include <string.h>

// Function to compute a simple hash using XOR and addition
void computeSimpleHash(const char *message, unsigned char *hash) {
    unsigned char temp = 0;

    // Simple hash computation: XOR and addition
    for (int i = 0; message[i] != '\0'; i++) {
        temp = temp ^ message[i];  // XOR each character
        temp += message[i];        // Add each character's value
    }
    
    // Store the result in the hash
    *hash = temp;
}

int main() {
    char message[256];      // Buffer for the input message
    unsigned char hash;     // Buffer for the hash (only 1 byte for simplicity)
    char receivedHash[3];   // Buffer for input of received hash (in hex format)

    printf("Enter the message: ");
    scanf("%s", message);

    computeSimpleHash(message, &hash);

    printf("Computed Hash (in hex): %02x\n", hash);

    printf("Enter the received hash (in hex): ");
    scanf("%s", receivedHash);

    unsigned int receivedHashValue;
    sscanf(receivedHash, "%02x", &receivedHashValue);

    if (hash == receivedHashValue) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}
~~~

## OUTPUT:
![image](https://github.com/user-attachments/assets/65bdb72e-96de-4db1-a673-ea3c116c4f70)


## RESULT:
The program for generating and verifying a simple hash of a given message using a custom hash function was executed successfully. The computed hash ensures basic integrity of the message.
