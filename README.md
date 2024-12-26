## Отчет по лабораторной работе № 3

#### № группы: `ПМ-2402`

#### Выполнила: `Каменева Алина Дмитриевна`

#### Вариант: `10`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Алгоритм](#2-алгоритм)
- [Программа](#3-программа)
- [Анализ правильности решения](#4-анализ-правильности-решения)

### 1. Постановка задачи

> Разработать программу для подсчёта голосов на выборах, где каждому кандидату со-
> ответствует количество голосов. Реализовать функции добавления, удаления и анализа
> данных, включая вычисление процентного распределения голосов между кандидатами.
> Данную задачу можно разделить на 5 подзадач:

Описание функционала

1. Создание списка кандидатов
   Создание пустого списка кандидатов и их голосов. Вывод списка в формате: «Кан-
   дидат: число голосов».
2. Добавление кандидата
   Добавление нового кандидата с начальным количеством голосов, равным нулю.
3. Добавление кандидата с голосами
   Добавление нового кандидата с заданным количеством голосов.
4. Поиск кандидата по имени
   Функция, которая возвращает индекс кандидата по его имени.
5. Удаление кандидата
   Удаление кандидата из списка по его имени.
6. Добавление голоса кандидату
   Увеличение количества голосов кандидата на единицу.
7. Добавление n голосов кандидату
   Увеличение количества голосов кандидата на заданное значение n.
8. Количество голосов кандидата
   Возвращает текущее количество голосов, набранных указанным кандидатом.
9. Общее количество голосов
   Подсчёт общего количества голосов, отданных за всех кандидатов.
10. Определение победителя
    Нахождение кандидата, набравшего наибольшее количество голосов.
11. Процент голосов кандидата
    Вычисление процента голосов, полученных кандидатом, от общего числа голосов.
12. Вывод таблицы с процентами голосов
    Отображение списка кандидатов в формате: «Кандидат - процент голосов».
13. Удаление кандидатов с низким количеством голосов
    Удаление всех кандидатов, набравших количество голосов или процент голосов
    ниже заданного порога.
14. Подсчёт голосов из массива имён
    Принимает массив имён кандидатов. Каждому кандидату из массива добавляется
    по одному голосу, моделируя процесс подсчёта бюллетеней.

### 2. Алгоритм

#### Алгоритм выполнения программы:

### 2. Описание классов и их методов

Для реализации функционала создано 2 класса: `Candidate`, `Election`, первый находится внутри второго .

1. Класс `Candidate`  
   Класс описывает кандидата выборов. Параметры: имя кандидата и количество голосов.

`name` - переменная типа `String`, которая хранит имя кандидата.

`volume` - переменная типа `int`, которая хранит кол-во страниц книги.

2. Класс `Election`  
   Класс описывает действия производящиеся над количеством голосов, их подсчетом, количеством кандидатов

`candidateCount` - переменная счетчик голосов.

`Candidate[] candidates` - массив, хранящий информацию о кандидатах.

### 2. Методы классов (разные операции)

Класс `Candidate` :

- Candidate(String name) - // задание кандидату имени и определение начального количества голосов
- Candidate(String name, int votes) // создание кандидата с именем и количеством голосов
- String getName() - // геттер для получения имени кандидата
- int getVotes() - // геттер для получения количества голосов
- void addVote() - // добавление одного голоса
- void addVotes(int n) - // добавление нескольких голосов
- double getVotePercentage(int totalVotes) - // вычисление процента голосов от общего числа

Класс `Election`

- Election(int maxCandidates) - // задаем начальное значение массиву кандидатов с заданным размером
- void addCandidate(String name) - // добавление нового кандидата с именем
- void addCandidate(String name, int votes) - // добавление нового кандидата с именем и количеством голосов
- int findCandidateIndex(String name) - // поиск индекса кандидата по имени
- void removeCandidate(String name) - // удаление кандидата по имени
- void addVote(String name) - // добавление одного голоса кандидату по имени
  void addVotes(String name, int n) - //добавление нескольких голосов кандидату по имени
- getCandidateVotes(String name) - // получение количества голосов у кандидата по имени
- int getTotalVotes() - // получение общего количества голосов всех кандидатов
- String getWinner() - //определение кандидата с максимальным количеством голосов (победителя)
- String GetPersent(String name) - // получение процента голосов, полученных кандидатом с заданным именем
- void displayVotePercentages() - // отображение процентов голосов каждого кандидата от общего количества голосов
- void removeLowScorers(double minPercentage) - // удаление кандидатов, у которых процент голосов ниже заданного порога
- void countVotesFromArray(String[] names) - // подсчет голосов из массива имен кандидатов
- void displayCandidates() - // отображение всех кандидатов и их голосов в консоли

### 5. Программа

```
import java.util.Scanner;
import java.io.PrintStream;
import static java.lang.System.out;
import static java.lang.System.setOut;

public class Main {
    public static Scanner in = new Scanner(System.in);
    public static PrintStream out = System.out;
    public static void main(String[] args) {

        // главная программа
    }
}

class Election { // определяем основной класс Election

    // внутренний класс Candidate для представления кандидата
    static class Candidate {
        private String name; // переменная, хранящая имя кандидата
        private int votes; // переменная, хранящая количество голосов

        // задание кандидату имени и определяем начальное количество голосов
        public Candidate(String name) {
            this.name = name; // имя кандидата
            this.votes = 0; // начальное количество голосов = 0
        }

        // создание кандидата с именем и количеством голосов
        public Candidate(String name, int votes) {
            this.name = name; // имя кандидата
            this.votes = votes; // устанавливаемое начальное количество голосов
        }

        // геттер для получения имени кандидата
        public String getName() {
            return this.name; // возвращаем имя кандидата
        }

        // геттер для получения количества голосов
        public int getVotes() {
            return this.votes; // возвращаем количество голосов
        }

        // добавление одного голоса
        public void addVote() {
            this.votes++; // увеличиваем количество голосов на 1
        }

        // добавление нескольких голосов
        public void addVotes(int n) {
            this.votes += n; // увеличиваем количество голосов на n
        }

        // вычисление процента голосов от общего числа
        public double getVotePercentage(int totalVotes) {
            if (totalVotes == 0) // если нет голосов, возвращаем 0
                return 0;
            return ((double) this.votes / totalVotes) * 100; // возвращаем процент голосов
        }

        //вывод информации о кандидате
        @Override
        public String toString() {
            return name + ": " + votes + " голосов";
        }
    }

    public Candidate[] candidates; // создаем пустой массив для хранения кандидатов
    public int candidateCount; // переменную для хранения текущего количество кандидатов

    //  задаем начальное значение массиву кандидатов с заданным размером
    public Election(int maxCandidates) {
        this.candidates = new Candidate[maxCandidates]; // создаем новый массив кандидатов с заданным количеством ячеек
        this.candidateCount = 0; // присваиваем переменной текущее количество кандидатов = 0
    }

    // добавление нового кандидата с именем
    public void addCandidate(String name) {
        if(this.candidateCount < candidates.length) {
            // проверяем, меньше ли текущее количество кандидатов максимального количества (длина массива candidates)
            if(this.candidateCount == 0) {  // если текущий счетчик кандидатов равен нулю, значит массив пуст
                this.candidates[this.candidateCount] = new Candidate(name); // создаем нового кандидата с заданным именем и добавляем его в массив по индексу candidateCount
                this.candidateCount++; // увеличиваем счетчик кандидатов на 1
            }
             else { // если в массиве уже есть кандидаты
                boolean flag = false; // флаг для проверки, существует ли кандидат с таким именем
                for(int i = 0; i < this.candidates.length - 1; i++) { // проходим по всем кандидатам в массиве (до предпоследнего элемента)
                    if(this.candidates[i] != null) { // проверяем, что текущий элемент массива не равен null (т.е. кандидат существует)
                        if(this.candidates[i].name.equals(name)) { // сравниваем имя текущего кандидата с заданным именем
                            flag = true; // устанавливаем флаг в true, если кандидат с таким именем найден
                            break; // выходим из цикла, так как кандидат найден
                }
            }
        }

        if(!flag) { // если флаг остался false, значит кандидат с таким именем не найден
            this.candidates[this.candidateCount] = new Candidate(name); // создаем нового кандидата с заданным именем и добавляем его в массив по индексу candidateCount
            this.candidateCount++; // увеличиваем счетчик кандидатов на 1
        }
    }
}

        }

    }

        // добавление нового кандидата с именем и количеством голосов
    public void addCandidate(String name, int votes) { // проверяем, меньше ли текущее количество кандидатов максимального количества
        if(this.candidateCount < candidates.length){ // если текущий счетчик кандидатов равен нулю, значит массив пуст
            if(this.candidateCount == 0){ // создаем нового кандидата с заданным именем и количеством голосов, и добавляем его в массив по индексу candidateCount
                this.candidates[this.candidateCount] = new Candidate(name, votes); // увеличиваем счетчик кандидатов на 1
                this.candidateCount ++;
            } else {
                boolean flag = false; // флаг для проверки, существует ли кандидат с таким именем

                // проходим по всем кандидатам в массиве (до предпоследнего элемента)
                for(int i = 0; i < this.candidates.length - 1; i ++){
                    // проверяем, что текущий элемент массива не равен null (т.е. кандидат существует)
                    if(this.candidates[i] != null){
                        // сравниваем имя текущего кандидата с заданным именем
                        if(this.candidates[i].name.equals(name)){
                            // устанавливаем флаг в true, если кандидат с таким именем найден
                            flag = true;
                            // выходим из цикла, так как кандидат найден
                            break;
                        }
                    }
                }

                // если флаг остался false, значит кандидат с таким именем не найден
                if(!flag){
                    // создаем нового кандидата с заданным именем и количеством голосов и добавляем его в массив по индексу candidateCount
                    this.candidates[this.candidateCount] = new Candidate(name, votes);
                    // увеличиваем счетчик кандидатов на 1
                    this.candidateCount ++;
                }
            }
        }
    }

    // поиск индекса кандидата по имени
    public int findCandidateIndex(String name) {
        for (int i = 0; i < this.candidateCount; i++) { // Проходим по массиву кандидатов до текущего количества кандидатов
            if (this.candidates[i].getName().equalsIgnoreCase(name)) { // с помощью геттера получаем имя и при помощи метода сравниваем имена (без учета регистра)
                return i; // возвращаем индекс найденного кандидата
            }
        }
        return -1; // если кандидат не найден, возвращаем -1
    }
    // удаление кандидата по имени
    public void removeCandidate(String name) {
        int index = findCandidateIndex(name); // находим индекс кандидата по имени
        if (index != -1) { // если кандидат найден
            for (int i = index; i < this.candidateCount - 1; i++) {
                this.candidates[i] = this.candidates[i + 1]; // сдвигаем всех последующих кандидатов на одну позицию влево
            }
            this.candidates[--this.candidateCount] = null; // уменьшаем количество кандидатов и обнуляем последний элемент
        }
    }

    // добавление одного голоса кандидату по имени
    public void addVote(String name) {
        int index = findCandidateIndex(name); // находим индекс кандидата по имени
        if (index != -1) { // если кандидат найден
            this.candidates[index].addVote(); // добавляем голос этому кандидату
        }
    }

    //добавление нескольких голосов кандидату по имени
    public void addVotes(String name, int n) {
        int index = findCandidateIndex(name); // находим индекс кандидата по имени
        if (index != -1) { // если кандидат найден
            this.candidates[index].addVotes(n); // добавляем n голосов этому кандидату
        }
    }

    // получение количества голосов у кандидата по имени
    public int getCandidateVotes(String name) {
        int index = findCandidateIndex(name); // находим индекс кандидата по имени
        if (index != -1) { // если кандидат найден
            return this.candidates[index].getVotes(); // возвращаем количество голосов этого кандидата
        }
        return -1; // если кандидат не найден, возвращаем -1
    }

    // получение общего количества голосов всех кандидатов
    public int getTotalVotes() {
        int total = 0; // создаем переменную для хранения общего количества голосов
        for (int i = 0; i < this.candidateCount; i++) { // перебор по всем кандидатам в массиве до текущего количества кандидатов
            total += this.candidates[i].getVotes(); // суммируем количество голосов каждого кандидата
        }
        return total; // возвращаем общее количество голосов
    }

    //определение кандидата с максимальным количеством голосов (победителя)
    public String getWinner() {
        Candidate winner = null; // переменная для хранения победителя
        for (int i = 0; i < this.candidateCount; i++) { // проходим по всем кандидатам в массиве
            if (winner == null || this.candidates[i].getVotes() > winner.getVotes()) {
                winner = this.candidates[i]; // обновляем победителя, если текущий кандидат имеет больше голосов
            }
        }
        if (winner != null)
            return  winner.getName(); // возвращаем имя победителя
        else
            return "Нет кандидатов"; // возвращаем сообщение об отсутствии кандидатов
    }

    // получение процента голосов, полученных кандидатом с заданным именем
    public String GetPersent(String name) {
        // проверяем, есть ли кандидаты в списке (candidateCount больше 0)
        if(this.candidateCount > 0) {
            return String.format("%.2f", (this.candidates[this.findCandidateIndex(name)].votes / (double)this.getTotalVotes()) * 100.0) + " %";
            // находим индекс кандидата с заданным именем и рассчитываем процент его голосов, форматируем результат с двумя знаками после запятой и добавляем символ '%'

        }
        else {
        return "Список пуст"; // если список кандидатов пуст, возвращаем сообщение об этом
        }
    }

    // отображение процентов голосов каждого кандидата от общего количества голосов
    public void displayVotePercentages() {
        int totalVotes = getTotalVotes(); // записываем общее количество голосов в дополнительную переменную
        for (int i = 0; i < this.candidateCount; i++) { // проходим по всем кандидатам в массиве
            out.print(this.candidates[i].getName() + " "); // выводим имя кандидата
            out.printf("%.2f%%\n", this.candidates[i].getVotePercentage(totalVotes)); // выводим его процент голосов с двумя знаками после запятой
        }
    }

    // удаление кандидатов, у которых процент голосов ниже заданного порога
    public void removeLowScorers(double minPercentage) {
        int totalVotes = getTotalVotes(); // записываем общее количество голосов в дополнительную переменную
        for (int i = 0; i < this.candidateCount; i++) { // проходим по всем кандидатам в массиве
            if (this.candidates[i].getVotePercentage(totalVotes) < minPercentage) { // проверяем, если процент голосов меньше минимума
                removeCandidate(this.candidates[i].getName()); // удаляем кандидата
                i--; // уменьшаем индекс, чтобы не пропустить следующего кандидата после удаления
            }
        }
    }

    // подсчет голосов из массива имен кандидатов
    public void countVotesFromArray(String[] names) {
        for (String name : names) { // проходим по каждому имени в массиве
            addVote(name); // добавляем голос соответствующему кандидату
        }
    }

    // отображение всех кандидатов и их голосов в консоли
    public void displayCandidates() {
        for (int i = 0; i < this.candidateCount; i++) { // проходим по всем кандидатам в массиве
            out.println(this.candidates[i]); // выводим информацию о каждом кандидате на экран
        }
    }

    @Override
    public String toString(){
        String ans = "";
        for(Candidate i: candidates){
            if(i != null){ // отбираем непустые элементы
                ans += i + "\n"; // выводим кандидата, переводим на новую строку
            }
        }
        return ans; // возвращаем результат
    }
}

```

### 6. Анализ правильности решения

Программа работает корректно на всем множестве решений.

1. Тест на проверку добавления одного, нескольких голосов и счетчика всех голосов:

   - **Input**:

     ````election.addCandidate("Кандидат 1");

     ``` election.addCandidate("Кандидат 2", 5);

     ```election.addVote("Кандидат 1");

     ```out.println("Общее количество голосов: " + election.getTotalVotes());

     ````

   - **Output**:

     ```Общее количество голосов: 6

     ```

2. Поиск индекса по имени:

   - **Input**:

     ```out.println("Индекс кандидата: " + election.findCandidateIndex("Кандидат 1"));

     ```

   - **Output**:

     ```Индекс кандидата: 0

     ```

3. Тест на определение победителя :

   - **Input**:

     ```out.println("Победитель: " + election.getWinner());

     ```

   - **Output**:

     ```Победитель: Кандидат 2

     ```

4. Тест на удаление кандидатов, не набравших нужное количество голосов:

   - **Input**:

     ```election.removeLowScorers(50.0);

     ```

   - **Output**:

     ```Кандидат 2: 5 голосов

     ```

5. Тест на вывод кандидатов с их количеством голосов в процентах:

   - **Input**:

     ```election.displayVotePercentages();

     ```

   - **Output**:

     ````Кандидат 1 16,67%
     ``` Кандидат 2 83,33%
     ````

6. Тест на добавление каждому кандидату из массива по 1 голосу:

   - **Input**:

     ````String[] votesArray = {"Кандидат 1", "Кандидат 2", "Кандидат 1"};
     ``` election.countVotesFromArray(votesArray);

     ````

   - **Output**:

   ````Кандидат 1: 3 голосов
   ``` Кандидат 2: 6 голосов
   ````