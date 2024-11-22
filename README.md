# act-age-imagen

#include <stdio.h>

// Declaración de yyin
extern FILE *yyin;

int main(int argc, char **argv) {
    if (argc > 1) {
        // Abrir el archivo pasado como argumento
        yyin = fopen(argv[1], "r");
        if (!yyin) {
            perror("No se pudo abrir el archivo");
            return 1;
        }
    } else {
        // Leer desde la entrada estándar
        printf("Introduce las líneas a derivar (Ctrl+D para finalizar):\n");
        yyin = stdin;
    }

    // Llamar al parser
    yyparse();

    if (argc > 1) {
        fclose(yyin);
    }

    return 0;
}
