19. Ширoков (Класс Complex) Создайте класс с именем Complex для выполнения  
арифметических операций с комплексными числами. Напишите программу для  
тестирования вашего класса. 
Комплексные числа имеют вид 
realPart + imaginaryPart * I, 
где i равно V-l. 
Используйте для представления закрытых данных класса переменные типа 
double. Определите конструктор, который дает возможность инициализировать 
объект класса при его объявлении. Конструктор должен содержать значения по 
умолчанию на случай отсутствия инициализаторов. Предусмотрите  
элемент-функции для каждого из следующих действий: 
a) Сложение двух чисел типа Complex: складываются вместе их вещественные 
части и их мнимые части. 
b) Вычитание двух чисел типа Complex: вещественная часть правого операнда 
вычитается из вещественной части левого операнда и мнимая часть правого 
операнда вычитается из мнимой части левого. 
c) Вывод чисел типа Complex в виде (а, Ь), где а — вещественная часть и b —
мнимая.

#include "StdAfx.h"
#include <iostream>
#include <conio.h>
#include <math.h>
#include <fstream>
using namespace std; 

class Complex // класс комплексных чисел
{
   double re, im; // целая и мнимая части
 
// создаем конструкторы   
public:
 
   Complex() {};
 
   Complex (double r) // конструктор по умолчанию
   {
      re = r; 
    im = 0;
   }
 
   Complex (double r, double i) // конструктор по умолчанию
   {
      re = r; 
	  im = i;
   } 
 
   Complex (Complex &c) // конструктор копирования
   {
      re = c.re; 
	  im = c.im;
   }
 
   ~Complex() {}
 
   float abs() // Модуль комплексного числа
   {
      return sqrt(re * re - im * im);
   }     
 
   Complex & operator = (Complex &c) // перегрузка оператора присваивания
   {
      re = c.re;
	  im = c.im;
 
	  return (*this);
   }
 
   Complex Complex::operator + (Complex &c) // перегрузка оператора сложения
   {
	  Complex temp;
 
	  temp.re = re + c.re;
	  temp.im = im + c.re;
 
	  return temp;
   }
 
   Complex Complex::operator - (Complex &c) // перегрузка оператора вычитания
   {
	  Complex temp;
 
	  temp.re = re - c.re;
	  temp.im = im - c.re;
 
	  return temp;
   }
 
   Complex Complex::operator * (Complex &c) // перегрузка оператора умножения
   {
	  Complex temp;
 
	  temp.re = re*c.re;
	  temp.im = re*c.im;
 
	  return temp;
   }
 
   Complex Complex::operator / (Complex &c) // перегрузка оператора деления
   {
	  Complex temp;
 
	  double r = c.re * c.re + c.im * c.im;
	  temp.re = (re * c.re + im * c.im) / r;
	  temp.re = (im * c.re - re * c.im) / r;
 
	  return temp;
   }   
 
   friend ostream &operator<<(ostream &, Complex &); // перегрузка оператора <<
   friend istream &operator>>(istream &, Complex &); // перегрузка оператора >>
 
};
 
ostream &operator<<(ostream &out, Complex &c)
{
   out << "(" << c.re << ") + I (" << c.im << "\n";
 
   return out;
}
 
istream &operator>>(istream &in, Complex &c)
{
   in >> c.re >> c.im;
 
   return in;
}
 
int main()
{
    Complex value1(5,2);
    Complex value2(3,-3);
 
    cout << value1 << " " << value2 << endl;
 
    cout << value1 + value2 << endl;
 
    cout << value1 - value2 << endl;
 
    cout << value1 * value2 << endl;
 
    cout << value1 / value2 << endl;    
 
    value1 = value2;
 
    cout << value1 << " = " << value2 << endl;
 system ("pause");
    return 0;
	

}

