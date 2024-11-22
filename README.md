# act-age-imagen

asignacion
    : ID ASIGNACION expresion {
          Simbolo *var = buscar_simbolo($1);
          if (!var) {
              yyerror("Error: Variable no declarada.");
          } else if (var->es_constante) {
              yyerror("Error: No se puede asignar a una constante.");
          } else {
              if (var->tipo == TIPO_INT) {
                  var->valor.valor_entero = atoi($3);
                  printf("Asignación: %s := %d\\n", $1, var->valor.valor_entero);
              } else if (var->tipo == TIPO_STRING) {
                  free(var->valor.valor_string);
                  var->valor.valor_string = strdup($3);
                  printf("Asignación: %s := %s\\n", $1, var->valor.valor_string);
              }
          }
      }
    ;
