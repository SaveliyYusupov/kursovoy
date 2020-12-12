#include<iostream>
#include <string>
#include <time.h>
#include<cstdlib>
#include <cstdlib>
#include<iomanip>
using namespace std;

int inputInt(int left_r, int right_r);//считывание вводимого значения типа int
bool isNumeric();//проверка на соответствие численному формату
bool isRange(int number, int left_r, int right_r);//проверка на принадлежность к указанному промежутку значений
class Time
{
public:
	int hour;
public:
	Time getCurrentTime()
	{
		struct tm localtime;
		time_t now = time(NULL);
		localtime_s(&localtime, &now);
		Time currentTime;
		currentTime.hour = localtime.tm_hour;
		return currentTime;
	}
	void greeting(Time time)
	{
		if (time.hour > 0 && time.hour < 13)
			cout << "Доброе утро! ";
		if (time.hour < 16 && time.hour >= 13)
			cout << "Добрый день! ";
		if (time.hour < 23 && time.hour >= 18)
			cout << "Добрый вечер! ";
	}
	friend void Greeting();
};
class Ticket
{
private:
	int no_trip;
	string type;
	string destination;
	string date;
	string time;
	int price;
	int left;
	int sold;
public:
	void getData()
	{
		cout << "Введите номер рейса: " << endl;
		cin >> no_trip;
		cout << "Введите тип транспортного средства: " << endl;
		getline(cin, type);
		cout << "Введите цель прибывания: " << endl;
		getline(cin, destination);
		cout << "Введите дату отправления: " << endl;
		getline(cin, date);
		cout << "Введите время отправления: " << endl;
		getline(cin, time);
		cout << "Введите цену за билет: " << endl;
		cin >> price;
		cout << "Введите количество билетов для покупки: " << endl;
		cin >> left;
		sold = 0;
	}
	void printData()
	{
		cout << no_trip << " " << type << " " << destination << " " << date << " " << time << " " << price << " " << left << " " << sold << endl;
	}
	void setNo()
	{
		cin >> no_trip;
	}
	void printNo()
	{
		cout << no_trip;
	}
	void setType()
	{
		getline(cin, type);
	}
	void printType()
	{
		cout << type;
	}
	void setDest()
	{
		getline(cin, destination);
	}
	void printDest()
	{
		cout << destination;
	}
	void setDate()
	{
		getline(cin, date);
	}
	void printDate()
	{
		cout << date;
	}
	void setTime()
	{
		getline(cin, time);
	}
	void printTime()
	{
		cout << time;
	}
	void setPrice()
	{
		cin >> price;
	}
	void printPrice()
	{
		cout << price;
	}
	void setLeft()
	{
		cin >> left;
	}
	void printLeft()
	{
		cout << left;
	}
	void setSold()
	{
		sold = 0;
	}
	void printSold()
	{
		cout << sold;
	}
	friend void searchTno(Ticket** arr_of_tickets, int boofNo, int number_of_tickets);
	friend void searchTtype(Ticket** arr_of_tickets, string boofType, int number_of_tickets);
	friend void searchTdest(Ticket** arr_of_tickets, string boofDest, int number_of_tickets);
	friend void searchTdate(Ticket** arr_of_tickets, string boofData, int number_of_tickets);
	friend void searchTprice(Ticket** arr_of_tickets, int boofPrice, int number_of_tickets);
	friend void showTList(Ticket** arr_of_tickets, int number_of_tickets);
	friend void addTicket(Ticket** arr_of_tickets, int& number_of_tickets);
	friend void deleteT(Ticket** arr_of_stickets, int& number_of_tickets, int number_to_deleteT);
};
//class Lecturer 
//{
//private:
//	string fio;
//	string degree;
//	string chair;
//	int number_of_publs;
//public:
//	void getData() 
//	{
//		cout << "Введите ФИО преподавателя: ";
//		getline(cin, fio);
//		cout << "Введите квалификацию преподавателя: ";
//		getline(cin, degree);
//		cout << "Введите название кафедры: ";
//		getline(cin, chair);
//		cout << "Введите количество опубликованных работ: ";
//		number_of_publs = inputInt(1, 150);
//	}
//	void printData() 
//	{
//		cout << fio << " " << degree << " " << chair << " " << number_of_publs << endl;
//	}
//	void setFio() 
//	{
//		getline(cin, fio);
//	}
//	void printFio() 
//	{
//		cout << fio;
//	}
//	void setDegree() 
//	{
//		getline(cin, degree);
//	}
//	void printDegree() 
//	{
//		cout << degree;
//	}
//	void setChair() 
//	{
//		getline(cin, chair);
//	}
//	void printChair() 
//	{
//		cout << chair;
//	}
//	void setN() 
//	{
//		number_of_publs = inputInt(1, 150);
//	}
//	void printN() 
//	{
//		cout << number_of_publs;
//	}
//	friend void searchLFio(Lecturer** arr_of_lecturers, string boofLFio, int number_of_lecturers);
//	friend void searchLChair(Lecturer** arr_of_lecturers, string boofchair, int number_of_lecturers);
//	friend void searchLSp(Lecturer** arr_of_lecturers, string boofSpesh, int number_of_lecturers);
//	friend void searchLP(Lecturer** arr_of_lecturers, int boofNPubls, int number_of_lecturers);
//	friend void addLecturer(Lecturer** arr_of_lecturers, int& number_of_lecturers);
//	friend void deleteL(Lecturer** arr_of_lecturers, int& number_of_lecturers, int number_to_deleteL);
//	friend void showLectList(Lecturer** arr_of_lecturers, int number_of_lecturers);
//};
//функции интерфейса
void Greeting();
void menu();
void m();
void m1();
void m2();
void m3();
void m4();
void m5();
void m6();
void m7();
void m8();
void m9();
void m10();
void m11();
void m12();
void printLine();
const string st1 = "Увы, ничего не найдено!", st2 = "Результаты поиска: ", st3 = "Данные успешно изменены!", st4 = "Редактируемые данные:\n", st5 = "Запись успешно удалена!\n";
const int SIZE_S = 2;
const int SIZE_L = 2;
int main()
{
	system("chcp 1251");
	Greeting();
	int choice2, choice3, choice4, choice5, choice6, choice7, choice8, choice9, choice10, choice11, choice12;
	int numb_to_editT, numb_to_editL, boofNo, boofnumb, boofNPubls, number_to_deleteS, number_to_deleteL;
	string  boofF, boofSp, boofLFio, boofchair, boofSpesh;
	int number_of_tickets = 0;
	Ticket* arr_of_tickets[SIZE_S];
	//добавляем исходные списки преподов и студентов
	m();
	bool flag1 = true;
	bool flag2 = true;
	bool flag3 = true;
	cout << "Заполните список билетов:\n";
	addTicket(arr_of_tickets, number_of_tickets);
	while (flag1 == true)
	{
		m1();
		choice2 = inputInt(0, 1);
		switch (choice2)
		{
		case 0:try
		{
			addTicket(arr_of_tickets, number_of_tickets);
		}
			  catch (const char* msg)
			  {
				  cout << msg << endl;
				  flag1 = false;
			  } break;
		case 1: flag1 = false; break;
		}
	}
	m2();
	while (flag3 == true)
	{
		menu();
		choice4 = inputInt(0, 5);
		switch (choice4)
		{
		case 1:cout << "Список студентов:\n";
			try
			{
				showTList(arr_of_tickets, number_of_tickets);
			}
			catch (const char* msg)
			{
				cout << msg << endl;
			}
		case 2: choice5 = 1;
			switch (choice5)
			{
			case 1:try
			{
				addTicket(arr_of_tickets, number_of_tickets);
			}
				  catch (const char* msg)
				  {
					  cout << msg << endl;
				  }break;
			}
			break;
		case 3:m4(); choice6 = inputInt(1, 2);
			switch (choice6)
			{
			case 1:m5(); int numb_to_editT = inputInt(0, number_of_tickets);
				cout << "Билет: "; arr_of_tickets[numb_to_editT]->printData(); cout << endl;
				m6(); choice7 = inputInt(1, 6);
				switch (choice7)
				{
				case 1:cout << st4; arr_of_tickets[numb_to_editT]->printNo(); cout << endl;
					cout << "Введите новый номер рейса: ";
					arr_of_tickets[numb_to_editT]->setNo();
					cout << st3 << endl; break;
				case 2:cout << st4; arr_of_tickets[numb_to_editT]->printType(); cout << endl;
					cout << "Введите новый тип рейса: ";
					arr_of_tickets[numb_to_editT]->setType(); cout << st3 << endl; break;
				case 3:cout << st4; arr_of_tickets[numb_to_editT]->printDest(); cout << endl;
					cout << "Введите новую конечную точку маршрута: ";
					arr_of_tickets[numb_to_editT]->setDest(); cout << st3 << endl; break;
				case 4:cout << st4; arr_of_tickets[numb_to_editT]->printDate(); cout << endl;
					cout << "Введите новую дату отправления: ";
					arr_of_tickets[numb_to_editT]->setDate(); cout << st3 << endl; break;
				case 5:cout << st4; arr_of_tickets[numb_to_editT]->printTime(); cout << endl;
					cout << "Введите время отправления: ";
					arr_of_tickets[numb_to_editT]->setTime(); cout << st3 << endl;  break;
				case 6:cout << st4; arr_of_tickets[numb_to_editT]->printPrice(); cout << endl;
					cout << "Введите новую цену за билет: ";
					arr_of_tickets[numb_to_editT]->setPrice(); cout << st3 << endl; break;
				case 7:cout << st4; arr_of_tickets[numb_to_editT]->printLeft(); cout << endl;
					cout << "Введите количество оставшихся для покупки билетов: ";
					arr_of_tickets[numb_to_editT]->setLeft();
					arr_of_tickets[numb_to_editT]->setSold(); cout << st3 << endl;
					break;
				}break;
			}break;
		case 4:m9(); choice9 = 1;
			switch (choice9)
			{
			case 1: m10(); choice10 = inputInt(1, 5); switch (choice10)
			{
			case 1:cout << "Введите искомый номер рейса: "; getline(cin, boofNo);
				cout << st2;
				searchTno(arr_of_tickets, boofNo, number_of_tickets);
				break;
			case 2:cout << "Введите искомую специальность: "; getline(cin, boofSp);
				cout << st2;
				searchSSp(arr_of_students, boofSp, number_of_students);
				break;
			case 3:cout << "Введите номер курса: ";  boofY = inputInt(1, 4);
				cout << st2;
				searchSY(arr_of_students, boofY, number_of_students);
				break;
			case 4:cout << "Введите средний балл: "; cin >> boofGpa;
				cout << st2;
				searchSGpa(arr_of_students, boofGpa, number_of_students);
				break;
			case 5:cout << "Введите искомую форму обучения: "; cin >> boofK_b;
				cout << st2;
				searchSK_b(arr_of_students, boofK_b, number_of_students);
				break;
			case 6:cout << "Введите номер зачетной книжки: ";  boofnumb = inputInt(1000000, 9999999);
				cout << st2;
				searchSnumb(arr_of_students, boofnumb, number_of_students);
				break;
			}break;
			case 2:m11(); choice11 = inputInt(1, 4);
				switch (choice11)
				{
				case 1:cout << "Введите искомое ФИО: "; getline(cin, boofLFio);
					cout << st2;
					searchLFio(arr_of_lecturers, boofLFio, number_of_lecturers);
					break;
				case 2:cout << "Введите искомую квалификацию: "; getline(cin, boofSpesh);
					cout << st2;
					searchLSp(arr_of_lecturers, boofSpesh, number_of_lecturers);
					break;
				case 3: cout << "Введите название кафедры: "; getline(cin, boofchair);
					cout << st2;
					searchLChair(arr_of_lecturers, boofchair, number_of_lecturers);
					break;
				case 4:cout << "Введите количество публикаций: "; boofNPubls = inputInt(1, 150);
					cout << st2;
					searchLP(arr_of_lecturers, boofNPubls, number_of_lecturers);
					break;
				}
				break;
			}
			break;
		case 5: 
			cout << "Введите номер билета в списке: "; int number_to_deleteT = inputInt(0, number_of_tickets);
				deleteT(arr_of_tickets, number_of_tickets, number_to_deleteT);
				break;
		}
		system("pause");
		return 0;
	}
	void deleteT(Ticket * *arr_of_tickets, int& number_of_tickets, int number_to_deleteT)
	{
		for (int i = number_to_deleteT; i < number_of_tickets - 1; i++)
		{
			arr_of_tickets[i] = arr_of_tickets[i + 1];
		}
		number_of_tickets--;
		cout << st5;
	}


	//добавление
	void addTicket(Ticket * *arr_of_tickets, int& number_of_tickets)
	{
		if (number_of_tickets == SIZE_S)
		{
			throw
				"Память заполнена! Очистите память!";
		}
		arr_of_tickets[number_of_tickets] = new Ticket;
		arr_of_tickets[number_of_tickets]->getData();
		number_of_tickets++;
		cout << "Данные успешно добавлены!\n";
	}
	//void addLecturer(Lecturer** arr_of_lecturers, int& number_of_lecturers) 
	//{
	//	if (number_of_lecturers == SIZE_L) 
	//	{
	//		throw
	//			"Память заполнена! Очистите память!\n";
	//	}
	//	arr_of_lecturers[number_of_lecturers] = new Lecturer;
	//	arr_of_lecturers[number_of_lecturers]->getData();
	//	number_of_lecturers++;
	//	cout << "Данные успешно добавлены!\n";
	//}
	void showTList(Ticket * *arr_of_tickets, int number_of_tickets)
	{
		if (number_of_tickets == 0)
		{
			throw
				"Список пуст!";
		}
		for (int i = 0; i < number_of_tickets; i++)
		{
			cout << i << ". "; arr_of_tickets[i]->printData();
			printLine();
		}
	}
	//void showLectList(Lecturer** arr_of_lecturers, int number_of_lecturers) 
	//{
	//	if (number_of_lecturers == 0) 
	//	{
	//		throw
	//			"Список пуст!";
	//	}
	//	for (int i = 0; i < number_of_lecturers; i++) 
	//	{
	//		cout << i << ". "; arr_of_lecturers[i]->printData();
	//		printLine();
	//	}
	//}

	void Greeting()
	{
		Time t1;
		t1.greeting(t1.getCurrentTime());
		cout << "Добро пожаловать в систему!\n";
	}
	void m()
	{
		cout << "База данных пуста! Для продолжения работы добавьте билеты.\n";
	}
	void printLine()
	{
		cout << "----------------------------------------------------------------------------------------" << endl;
	}
	void m1()
	{
		cout << "Хотите добавить еще одну запись?\n0-Да\n1-Нет\n";
	}
	void m2()
	{
		cout << "База данных заполнена. Приятной работы!\n";
	}
	void menu()
	{
		cout << "1-Просмотр данных.\n2-Добавление данных.\n3-Редактирование данных.\n4-Поиск данных.\n5-Удаление данных.\n6-Покупка билетов\n0-Выход из системы.\n";
	}
	void m3()
	{
		cout << "1-Добавление студента.\n2-Добавление преподавателя.\n";
	}
	void m4()
	{
		cout << "Перейти к редактированию списка\n1-студентов\n2-преподавателей\n";
	}
	void m5()
	{
		cout << "Введите номер билета в списке: ";
	}
	void m6()
	{
		cout << "Отредактировать\n1-Номер рейса\n2-Тип поездки\n3-Пункт прибытия\n4-Дату отправления\n5-Время отправления\n6-Цену за билет\n7-Количество билетов для покупки\n";
	}
	void m7()
	{
		cout << "Введите номер преподавателя в списке: ";
	}
	void m8()
	{
		cout << "Отредактировать\n1-ФИО преподавателя\n2-квалификацию\n3-название кафедры\n4-количество опубликованных работ\n";
	}
	void m9()
	{
		cout << "Осуществить поиск по\n1-списку студентов\n2-списку преподавателей\n";
	}
	void m10()
	{
		cout << "Поиск по \n1-Номеру рейса\n2-Типу поездки\n3-Пункту прибытия\n4-Дате отправления\n5-Цене за билет\n";
	}
	void m11()
	{
		cout << "Поиск по\n1-ФИО преподавателя\n2-квалификации\n3-названию кафедры\n4-количеству публикаций\n";
	}
	void m12()
	{
		cout << "1-Удаление из списка студентов.\n2-Удаление из списка преподавателей.\n";
	}
	bool isNumeric()
	{
		if (cin.get() == '\n')
			return true;
		else
		{
			cin.clear();
			cin.ignore(numeric_limits<streamsize>::max(), '\n');
			return false;
		}
	}
	bool isRange(int number, int left_r, int right_r)
	{
		if ((number >= left_r) && (number <= right_r))
			return true;
		else
			return false;
	}
	int inputInt(int left_r, int right_r)
	{
		int number;
		while (true)
		{
			cin >> number;
			if (isNumeric() && isRange(number, left_r, right_r))
				return number;
			else
				cout << "Извините, но Вы ввели некорректное значение. Пожалуйста, повторите ввод: ";
		}
	}
	//поиски для студентов
	void searchTtype(Ticket * *arr_of_tickets, string boofType, int number_of_tickets)
	{
		int counter = 0;
		for (int i = 0; i < number_of_tickets; i++)
		{
			if (arr_of_tickets[i]->fio == boofType)
			{
				arr_of_tickets[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchTprice(Ticket** arr_of_tickets, int boofPrice, int number_of_tickets) 
	{
		int counter = 0;
		for (int i = 0; i < number_of_tickets; i++)
		{
			if (arr_of_tickets[i]->fio == boofPrice)
			{
				arr_of_tickets[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchTdest(Ticket * *arr_of_tickets, string boofDest, int number_of_tickets)
	{
		int counter = 0;
		for (int i = 0; i < number_of_tickets; i++)
		{
			if (arr_of_tickets[i]->destination == boofDest)
			{
				arr_of_tickets[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchTdate(Ticket** arr_of_tickets, string boofDate, int number_of_tickets)
	{
		int counter = 0;
		for (int i = 0; i < number_of_tickets; i++)
		{
			if (arr_of_tickets[i]->date == boofDate)
			{
				arr_of_tickets[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchTtime(Ticket** arr_of_tickets, string boofDate, int number_of_tickets)
	{
		int counter = 0;
		for (int i = 0; i < number_of_tickets; i++)
		{
			if (arr_of_tickets[i]->date == boofDate)
			{
				arr_of_tickets[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchTno(Ticket * *arr_of_tickets, int boofNo, int number_of_tickets)
	{
		int counter = 0;
		for (int i = 0; i < number_of_tickets; i++)
		{
			if (arr_of_tickets[i]->year == boofNo)
			{
				arr_of_tickets[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchSGpa(Student * *arr_of_students, double boofGpa, int number_of_students)
	{
		int counter = 0;
		for (int i = 0; i < number_of_students; i++)
		{
			if (arr_of_students[i]->gpa == boofGpa)
			{
				arr_of_students[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchSK_b(Student * *arr_of_students, int boofK_b, int number_of_students)
	{
		int counter = 0;
		for (int i = 0; i < number_of_students; i++)
		{
			if (arr_of_students[i]->k_b == boofK_b)
			{
				arr_of_students[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchSnumb(Student * *arr_of_students, int boofnumb, int number_of_students)
	{
		int counter = 0;
		for (int i = 0; i < number_of_students; i++)
		{
			if (arr_of_students[i]->numb == boofnumb)
			{
				arr_of_students[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	//поиски для лекторов
	//void searchLFio(Lecturer * *arr_of_lecturers, string boofLFio, int number_of_lecturers)
	//{
	//	int counter = 0;
	//	for (int i = 0; i < number_of_lecturers; i++)
	//	{
	//		if (arr_of_lecturers[i]->fio == boofLFio)
	//		{
	//			arr_of_lecturers[i]->printData();
	//			counter++;
	//		}
	//	}
	//	if (counter == 0)
	//		cout << st1 << endl;
	//}
	/*void searchLChair(Lecturer * *arr_of_lecturers, string boofchair, int number_of_lecturers)
	{
		int counter = 0;
		for (int i = 0; i < number_of_lecturers; i++)
		{
			if (arr_of_lecturers[i]->chair == boofchair)
			{
				arr_of_lecturers[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchLSp(Lecturer * *arr_of_lecturers, string boofSpesh, int number_of_lecturers)
	{
		int counter = 0;
		for (int i = 0; i < number_of_lecturers; i++)
		{
			if (arr_of_lecturers[i]->degree == boofSpesh)
			{
				arr_of_lecturers[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}
	void searchLP(Lecturer * *arr_of_lecturers, int boofNPubls, int number_of_lecturers)
	{
		int counter = 0;
		for (int i = 0; i < number_of_lecturers; i++)
		{
			if (arr_of_lecturers[i]->number_of_publs == boofNPubls)
			{
				arr_of_lecturers[i]->printData();
				counter++;
			}
		}
		if (counter == 0)
			cout << st1 << endl;
	}*/

