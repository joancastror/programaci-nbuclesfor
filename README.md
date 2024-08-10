programación bucles for
 1) Dado un conjunto de datos representando las dimensiones de triángulos, calcular y contar aquellos cuya área excede un valor límite.

Código 
namespace Triangulos
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // Definir el límite para el área
                double areaLimite = 50.0;
                int contador = 0;

                // Matriz de triángulos (cada triángulo es representado por un array de tres lados)
                double[][] triangulos = new double[][]
                {
                    new double[] {3, 4, 5},
                    new double[] {10, 10, 10},
                    new double[] {7, 24, 25},
                    new double[] {15, 15, 20},
                    new double[] {9, 12, 15}
                };

                // Iterar sobre cada triángulo y calcular su área
                for (int i = 0; i < triangulos.Length; i++)
                {
                    double a = triangulos[i][0];
                    double b = triangulos[i][1];
                    double c = triangulos[i][2];

                    // Verificar si los lados forman un triángulo válido
                    if (EsTrianguloValido(a, b, c))
                    {
                        double area = CalcularArea(a, b, c);
                        Console.WriteLine($"El área del triángulo con lados {a}, {b}, {c} es: {area:F2}");

                        // Contar si el área excede el valor límite
                        if (area > areaLimite)
                        {
                            contador++;
                        }
                    }
                    else
                    {
                        Console.WriteLine($"Los lados {a}, {b}, {c} no forman un triángulo válido.");
                    }
                }

                Console.WriteLine($"\nNúmero de triángulos con un área superior a {areaLimite}: {contador}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Ocurrió un error: {ex.Message}");
            }
        }

        // Método para verificar si los lados forman un triángulo válido
        static bool EsTrianguloValido(double a, double b, double c)
        {
            return a + b > c && a + c > b && b + c > a;
        }

        // Método para calcular el área usando la fórmula de Herón
        static double CalcularArea(double a, double b, double c)
        {
            double s = (a + b + c) / 2;
            return Math.Sqrt(s * (s - a) * (s - b) * (s - c));
        }
    }
}
 

2) Crear un programa que cuente cuántos números, de un conjunto de 10, son divisibles por 3 o por 5.
namespace ContarDivisibles
{
    public class ContadorDivisibles
    {
        public void ContarDivisiblesPor3o5()
        {
            int[] numeros = new int[10];
            int contador = 0;

            try
            {
                // Leer los 10 números desde la consola
                for (int i = 0; i < numeros.Length; i++)
                {
                    Console.WriteLine($"Ingrese el número {i + 1}:");
                    string entrada = Console.ReadLine();

                    if (string.IsNullOrEmpty(entrada))
                    {
                        Console.WriteLine("El número es requerido.");
                        return;
                    }

                    if (!int.TryParse(entrada, out numeros[i]))
                    {
                        Console.WriteLine("Entrada inválida, ingrese un número entero.");
                        return;
                    }

                    // Verificar si el número es divisible por 3 o por 5
                    if (numeros[i] % 3 == 0 || numeros[i] % 5 == 0)
                    {
                        contador++;
                    }
                }

                // Mostrar el resultado
                Console.WriteLine($"\nCantidad de números divisibles por 3 o por 5: {contador}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Ocurrió un error: {ex.Message}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            ContadorDivisibles contadorDivisibles = new ContadorDivisibles();
            contadorDivisibles.ContarDivisiblesPor3o5();
        }
    }
}

 
3) Desarrollar un programa que permita ingresar 10 números y luego muestre la suma de los últimos 5 números ingresados.

namespace SumaUltimosCincoNumeros
{
    public class CalculadoraSuma
    {
        public void CalcularSumaUltimosCinco()
        {
            int[] numeros = new int[10];
            int suma = 0;

            try
            {
                // Ingresar los 10 números
                for (int i = 0; i < numeros.Length; i++)
                {
                    Console.WriteLine($"Ingrese el número {i + 1}:");
                    string entrada = Console.ReadLine();

                    if (string.IsNullOrEmpty(entrada))
                    {
                        Console.WriteLine("El número es requerido.");
                        return;
                    }

                    if (!int.TryParse(entrada, out numeros[i]))
                    {
                        Console.WriteLine("Entrada inválida, ingrese un número entero.");
                        return;
                    }
                }

                // Calcular la suma de los últimos 5 números
                for (int i = 5; i < numeros.Length; i++)
                {
                    suma += numeros[i];
                }

                // Mostrar la suma de los últimos 5 números
                Console.WriteLine($"\nLa suma de los últimos 5 números es: {suma}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Ocurrió un error: {ex.Message}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            CalculadoraSuma calculadoraSuma = new CalculadoraSuma();
            calculadoraSuma.CalcularSumaUltimosCinco();
        }
    }
}

 
