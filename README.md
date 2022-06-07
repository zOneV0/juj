#include <iostream>
#include <ctime>
#include <string>
#include <math.h>
#include <stdlib.h>
#include <fstream>
using namespace std;

class P
{
private:
	int hd1;
	int wins;
public:
	friend int game1(int hd1, int wins);
};

class C
{
private:
	int hd1;
	int wins;
public:
	friend int game1(int hd1, int wins);
};

int game1(int hd1, int wins)
{
	cout << hd1 << endl << wins << endl;
	return 0;
}



int main()
{
	int pos_x, pos_y, ii_x, ii_y, g1 = 0, z = 0;
	int x = 3, wins = 0, hd1 = 0;
	char mas[3][3];
	string wins1, stg;
	bool game = true, p_status = true, prog = true;
	char key, a = ' ', b, c, d;

	

	cout << "wins:";



	ofstream out;
	ifstream in("start.txt");
	string line;
	if (in.is_open())
	{
		while (getline(in, line))
		{
			cout << line << endl;

		}
	}
	wins = atoi(wins1.c_str());
	in.close();

	cout << "press any ket to start: ";
	cin >> stg;

	pos_x = 1;
	pos_y = 1;

	srand(time(NULL));

	for (int i = 0; i < x; i++)//заполнение массива
	{
		for (int j = 0; j < x; j++)
		{
			mas[i][j] = ' ';
		}
	}

	do
	{
		do
		{

			mas[pos_y][pos_x] = '*'; //игрок

			system("cls"); //очистка консоли

			for (int i = 0; i < x; i++) //вывод массива
			{
				cout << '|' << ' ';
				for (int j = 0; j < x; j++)
				{
					cout << mas[i][j] << ' ';
				}
				cout << '|' << endl;
			}
			game1(hd1, wins);
			cout << "input: ";
			cin >> key;
			//------------------------------------------------------------------------------------
					//ход компьютера
			while (p_status != true)
			{
				ii_x = rand() % 3;
				ii_y = rand() % 3;
				if ((mas[ii_y][ii_x] != 'O') && (mas[ii_y][ii_x] != 'X') && (ii_y <= 2) && (ii_x <= 2))
				{
					mas[ii_y][ii_x] = 'X';
					p_status = true;
				}
			}
			//------------------------------------------------------------------------------------
			if ((mas[0][0] == 'X') && (mas[0][1] == 'X') && (mas[0][2] == 'X'))  //верх
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;
			}
			else if ((mas[1][0] == 'X') && (mas[1][1] == 'X') && (mas[1][2] == 'X')) //середина
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;
			}
			else if ((mas[2][0] == 'X') && (mas[2][1] == 'X') && (mas[2][2] == 'X')) //низ
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;
			}
			//------------------------------------------------------------------------------------
			//проверка по вертикали
			else if ((mas[0][0] == 'X') && (mas[1][0] == 'X') && (mas[2][0] == 'X')) //лево
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;


			}
			else if ((mas[0][1] == 'X') && (mas[1][1] == 'X') && (mas[2][1] == 'X')) //середина
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;
			}
			else if ((mas[0][2] == 'X') && (mas[1][2] == 'X') && (mas[2][2] == 'X')) //право
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;
			}
			//------------------------------------------------------------------------------------
			//проверка по диагонали
			else if ((mas[0][0] == 'X') && (mas[1][1] == 'X') && (mas[2][2] == 'X')) //лево верх
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;
			}
			else if ((mas[0][2] == 'X') && (mas[1][1] == 'X') && (mas[2][0] == 'X')) //право верх
			{
				cout << endl << "\t" << "\t" << "You lose";
				game = false;
				hd1++;
			}
			//------------------------------------------------------------------------------------
			//управление
			if (game == true)
			{
				if (key == 'a')
				{
					if (pos_x > 0)
					{
						mas[pos_y][pos_x] = a;
						a = mas[pos_y][pos_x - 1];
						pos_x -= 1;
					}
				}

				else if (key == 'd')
				{
					if (pos_x < 2)
					{
						mas[pos_y][pos_x] = a;
						a = mas[pos_y][pos_x + 1];
						pos_x += 1;
					}
				}

				else if (key == 'w')
				{
					if (pos_y > 0)
					{
						mas[pos_y][pos_x] = a;
						a = mas[pos_y - 1][pos_x];
						pos_y -= 1;
					}
				}

				else if (key == 's')
				{
					if (pos_y < 2)
					{
						mas[pos_y][pos_x] = a;
						a = mas[pos_y + 1][pos_x];
						pos_y += 1;
					}
				}
				//-----------------------------------------------------------------------------------
				//ход игрока
				else if (key == '0')
				{
					if (a != 'X')
					{
						mas[pos_y][pos_x] = 'O';
						p_status = false;
						a = 'O';
					}

				}
				//------------------------------------------------------------------------------------
				//проверка по горизонтали
				if ((mas[0][0] == 'O') && (mas[0][1] == 'O') && (mas[0][2] == 'O'))  //верх
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				else if ((mas[1][0] == 'O') && (mas[1][1] == 'O') && (mas[1][2] == 'O')) //середина
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				else if ((mas[2][0] == 'O') && (mas[2][1] == 'O') && (mas[2][2] == 'O')) //низ
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				//------------------------------------------------------------------------------------
				//проверка по вертикали
				else if ((mas[0][0] == 'O') && (mas[1][0] == 'O') && (mas[2][0] == 'O')) //лево
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				else if ((mas[0][1] == 'O') && (mas[1][1] == 'O') && (mas[2][1] == 'O')) //середина
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				else if ((mas[0][2] == 'O') && (mas[1][2] == 'O') && (mas[2][2] == 'O')) //право
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				//------------------------------------------------------------------------------------
				//проверка по диагонали
				else if ((mas[0][0] == 'O') && (mas[1][1] == 'O') && (mas[0][2] == 'O')) //лево верх
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				else if ((mas[0][2] == 'O') && (mas[1][1] == 'O') && (mas[2][0] == 'O')) //право верх
				{
					cout << endl << "\t" << "\t" << "You win";
					game = false;
					wins++;
					out.open("start.txt");
					if (out.is_open())
					{
						out << endl << wins << endl;
					}
				}
				//--------------------------------------------------------------------------------------
			}
		} while (game == true);
		cout << endl << endl;
		cout << "press any key to restart: ";
		cin >> stg;
		game = true;
		if (stg == "iop")
		{
			game = false;
			prog = false;
		}
		for (int i = 0; i < x; i++)//заполнение массива
		{
			for (int j = 0; j < x; j++)
			{
				mas[i][j] = ' ';
			}
		}

	} while (prog == true);


}


