# lab01- sumador 
## nombres

## informe de laoratorio 

### sumador 

```verilog
module sum1bcc_primitive (A, B, Ci, Cout, S);

  // Declaración de puertos de entrada
  input  A;   // Primer bit de entrada
  input  B;   // Segundo bit de entrada
  input  Ci;  // Acarreo de entrada
  
  // Declaración de puertos de salida
  output Cout; // Acarreo de salida
  output S;    // Resultado de la suma

  // Declaración de cables intermedios
  wire a_ab;    // Cable para el resultado de AND entre A y B
  wire x_ab;    // Cable para el resultado de XOR entre A y B
  wire cout_t;  // Cable para el acarreo temporal

  // Operación AND entre A y B
  and(a_ab, A, B);

  // Operación XOR entre A y B
  xor(x_ab, A, B);

  // Operación XOR entre el resultado de XOR anterior y Ci
  xor(S, x_ab, Ci);

  // Operación AND entre el resultado de XOR anterior y Ci
  and(cout_t, x_ab, Ci);

  // Operación OR entre el acarreo temporal y el resultado de AND entre A y B
  or (Cout, cout_t, a_ab);

endmodule
```
