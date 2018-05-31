# Elite-education

####################################################

		Первая задача с ACMP
			
####################################################

На доске написана последовательность n целых чисел. Играют двое. 
На очередном ходе игрок выбирает число с правого или с левого края последовательности.
Затем это число стирается и последовательность становится на одно число меньше, а ход переходит к противнику.
Выигрывает тот, кто наберет в сумме больше.
Написать программу, определяющую победителя в конкретной игре, при условии, что игроки будут играть оптимально.

Входные данные:
В первой строке входного файла INPUT.TXT записано целое число n(0 < n < 100).
Во второй строке через пробел заданы n натуральных чисел, не превосходящих 1000.

Выходные данные:
В единственную строку выходного файла OUTPUT.TXT нужно вывести 1, если победит первый игрок, 
2– если победит второй игрок и 0 – в случае ничьей.

	#include <iostream>
	#include <fstream>
	#include <conio.h>		
	#include <stdio.h>		
	using namespace std;	

	void main()					 
	{
	setlocale(LC_ALL, "Rus");

	ifstream INPUT("INPUT.TXT");
	ofstream OUTPUT("OUTPUT.TXT");

	int n;
	INPUT >> n;
	int *Array= new int[n];
	
	for (int i = 0; i < n; i++) INPUT >> Array[i];
	
	int Player_1 = 0;
	int Player_2 = 0;
	int a = n - 1;
	cout << "n = " << n << "\n";
	cout << "Начальный ряд чисел:\n";
	
	for (int i = 0; i < a+1; i++) cout << Array[i] << " ";

	for (int i = 0; i < n / 2; i++)
	{
		if (Array[0] < Array[a])
		{	
			Player_1 += Array[a];
			cout << "\nНаибольшее крайнее число = " << Array[a];
			a--;
		}
		else if (Array[0] >= Array[a])
		{
			Player_1 += Array[0];
			cout << "\nНаибольшее крайнее число = " << Array[0];
			for (int j = 0; j < a; j++)Array[j] = Array[j + 1];		
			a--;
		}

		cout << "\nИгрок 1: " << Player_1 << "\n\n";
		cout << "Получившийся ряд чисел:\n";
		for (int i = 0; i < a + 1; i++) cout << Array[i] << " ";

		if (Array[0] < Array[a])
		{
			Player_2 += Array[a];
			cout << "\nНаибольшее крайнее число = " << Array[a];
			a--;
		}
		else if (Array[0] >= Array[a])
		{
			Player_2 += Array[0];
			cout << "\nНаибольшее крайнее число = " << Array[0];
			for (int j = 0; j < a; j++) Array[j] = Array[j + 1];			
			a--;
		}
		cout << "\nИгрок 2: " << Player_2 << "\n";
		cout << "\nПолучившийся ряд чисел:\n";
		for (int i = 0; i < a + 1; i++) cout << Array[i] << " ";
	}

	if (n % 2 != 0)
	{
		Player_1 += Array[a];
		cout << "\nИгрок 1: " << Player_1 << "\n";
	}

	cout << "\nРезультат:\n";
	if (Player_1 > Player_2) { OUTPUT << 1; cout << "Победа игрока 1"; }
	else if (Player_2 > Player_1) {OUTPUT << 2; cout << "Победа игрока 2";}
	else { OUTPUT << 0; cout << "Ничья"; }

	cout << "\n";
	system("pause");
	}
	
	


####################################################

	  Динамический односвязный список
			
####################################################
	
С использованием структур данных(struct) реализовать на языке С++ программу для заполнения списка элементов и поиска элемента по заданному критерию.
Для этого самостоятельно реализовать динамический список и операции по его обработке.

	#include <iostream>
	#include <conio.h>
	#include <vector>
	#include <string> 

	using namespace std;
	void main();
	struct Property
	{
	
	double Weight;
	double Height;
	double Years;

	Property *next;									// Ссылка на следующий элемент списка
	};

	class Human
	{	
	Property * link;

	public:
	int i;
	Human(){ i = 0; } //:link(NULL) {}
	~Human();

	void Component_IN(double, double, double);
	void Component_OUT(int);
	void OutputALL();
	void Search(int, int);
	};
	void Human::Component_IN(double Weight, double Height, double Years)	// Создание нового элемента списка
	{
	Property *p = new Property;
	p->Weight = Weight;
	p->Height = Height;
	p->Years = Years;
	p->next = link;
	link = p;
	}

	void Human::Component_OUT(int n)
	{
	Property *temp = link;
	for (int i = 0; i<n;i++) temp = temp->next;
	
	cout << n << " человек:\n";
	cout << "Вес " << temp->Weight << "\n";
	cout << "Рост " << temp->Height << "\n";
	cout << "Возраст " << temp->Years << "\n\n";
	}

	void Human::OutputALL()
	{
	system("cls");
	Property *temp = link;
	while (temp)
	{
		i++;
		cout << "Характеристики "<< i << " человека:\n";
		cout << "Вес " << temp->Weight << "\n";
		cout << "Рост " << temp->Height << "\n";
		cout << "Возраст " << temp->Years << "\n\n";

		temp = temp->next;
	}
	_getch();
	main();
	}


	void Human::Search(int mode, int N)
	{	
	int i = 0;
	int a = 0;
	double SearchingValue;	
	double *Result = new double[N];
	system("cls"); 
	cout << "Введие значение:\n";
	cin >> SearchingValue;
	Property *temp = link;
	switch (mode)
	{
		case 1:									// По весу
		{
			while (temp)
			{
				i++;
				if (SearchingValue == temp->Weight)
				{
					Result[a] = i;
					a++;
				}
				temp = temp->next;
			}

			break;
		}
		case 2:									// По росту
		{
			while (temp)
			{
				i++;
				if (SearchingValue == temp->Height)
				{
					Result[a] = i;
					a++;
				}
				temp = temp->next;
			}

			break;	
		}
		case 3:									// По возрасту
		{
			while (temp)
			{
				i++;
				if (SearchingValue == temp->Years)
				{
					Result[a] = i;
					a++;
				}
				temp = temp->next;
			}

			break;
		}
	}

	cout << "Список совпадений:\n\n";
	for (int i = 0; i < a; i++)
	{
		Component_OUT( Result[i]) ;
	}
	_getch();
	main();
	}

	Human::~Human()
	{
	Property* temp = link;
	while (temp)
	{
		Property* del = temp;
		temp = temp->next;
		delete del;
	}
	}

	void main()
	{
	setlocale(0, "rus");
	Human *list;
	list = new Human;						// Выделение памяти под динамический список

	double Weight;
	double Height;
	double Years;
	int N = 12;
	for (int i = 0; i<N;i++)
	{
		Weight = rand() % 13 + 10;
		Height = rand() % 13 + 10;
		Years = rand() % 13 + 10;
		list->Component_IN(Weight, Height, Years);
	}


	int counter, chosen_option;
	counter = 1;
	chosen_option = 1;
	vector<string> options;

	options.push_back("Вывести весь список\n");
	options.push_back("Поиск по весу\n");
	options.push_back("Поиск по росту\n");
	options.push_back("Поиск по возрасту\n");
	options.push_back("Выход из программы");

	char pressed;
	do
	{
		system("cls");

		cout << "\t\tСписок пациентов\n\n";

		for (size_t i = 0; i < options.size(); ++i)
		{
			if ((i + 1) == counter)cout << "-> " << options[i];
			else cout << options[i];
		}


		cout << "\nДля выхода из программы нажмите Esc";

		pressed = _getch();

		if (pressed == 72 && counter != 1)
			counter--;
		if (pressed == 80 && counter != options.size())
			counter++;
		if (pressed == 27) exit(0);

	} while (pressed != 13);

	switch (counter)
	{
	case 1:
	{
		list->OutputALL();
		break;
	}
	case 2:
	{
		list->Search(1, N);
		break;
	}

	case 3:
	{
		list->Search(2, N);
		break;
	}
	case 4:
	{
		list->Search(3, N);
		break;
	}
	case 5:
	{
		exit(0);
		break;
	}
	}
	_getch();	
	delete list;
	}
