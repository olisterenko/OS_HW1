### Листеренко Ольга Руслановна ###
### БПИ 217 ###
  
### Вариант 20 ###
### Задача ###
Разработать программу, вычисляющую **число вхождений различных цифр** в заданной ASCII-строке.  

### Общая информация о тестировании ###
Тесты можно найти в папке Tests. Для каждой оценки сформированы собственные выходные файлы, они находятся в папке N/Outputs, где N — оценка. Число в названии тестового файла соответствует числу в названии файла-результата. 

#### Тест 3 ####  
В файле 5499 символов (500 строк по 11 символов, включая '\n', кроме последней строки).

#### Тест 4 ####  
В файле 5000 символов. 

#### Тест 5 ####  
Пустой файл. 
  
### 4 балла ###
Разработка программы, осуществляющей взаимодействие между тремя *дочерними* процессами с использованием *неименованных* каналов.  
   
#### Общая схема решаемой задачи ####
Первый процесс создает неименованный канал, а затем происходит форк. После форка первый процесс открывает и читает заданный файл, закрывает его и передает содержимое в неименованный канал. Второй процесс создает еще один неименованный канал и тоже делает форк, а затем принимает данные из первого неименованного канала, обрабатывает их и передает результат вычислений во второй неименованный канал. Третий процесс забирает массив из второго неименованного канала, открывает файл для вывода и выполняет вывод в него, затем файл закрывает.  
  
#### О программе ####
Разработано консольное приложение в соответствии с заданием. Код в файле 4/4_task.c. Имена входного и выходного файлов задаются в качестве аргументов командной строки (./4_task input.txt output.txt). Чтение и запись в файлы происходит через системные вызовы read и write. Буфер для данных из файла и чтения из первого пайпа имеет размер 5000. Для хранения результатов обработки используется целочисленный массив на 10 значений int (нет смысла хранить больше).
  
#### Тестрирование ####
В папке Tests представлен набор из 7 текстовых файлов, на которых проводилось тестирование. Для каждого теста в папке 4/Outputs представлен файл, полученный в результате работы программы.  
  
### 5 баллов ###
Разработка программы, в которой взаимодействие между тремя *дочерними* процессами осуществляется через *именованные* каналы. 
   
#### Общая схема решаемой задачи ####
Первый процесс пытается создать именованный канал "listerenko1.fifo" с помощью системного вызова mknod (если канал уже был создан, программа завершится, тогда его надо удалить), затем происходит форк. После форка первый процесс открывает и читает заданный файл, закрывает его и открывает именнованный канал, в который передает содержимое файла. Второй процесс создает еще один именованный канал "listerenko2.fifo" с помощью системного вызова mknod и тоже делает форк, а затем открывает первый именнованный канал и принимает данные из него, затем открывает второй именованный канал, обрабатывает данные из первого и передает результат вычислений во второй канал. Третий процесс открывает второй именованный канал и считывает массив, открывает файл для вывода и выполняет вывод в него, затем файл закрывает.  
  
#### О программе ####
Разработано консольное приложение в соответствии с заданием. Код в файле 5/5_task.c. Имена входного и выходного файлов задаются в качестве аргументов командной строки (./5_task input.txt output.txt). Чтение и запись в файлы происходит через системные вызовы read и write. Буфер для данных из файла и чтения из первого именованного канала имеет размер 5000. Для хранения результатов обработки используется целочисленный массив на 10 значений int.  
  
#### Тестрирование ####
В папке Tests представлен набор из 7 текстовых файлов, на которых проводилось тестирование. Для каждого теста в папке 5/Outputs представлен файл, полученный в результате работы программы.  
  
### 6 баллов ###
Разработка программы, осуществляющей взаимодействие между двумя *дочерними* процессами с использованием *неименованных* каналов.  
   
#### Общая схема решаемой задачи ####
Первый процесс создает два неименнованных (в критериях просят в отчете указать имена каналов, но требуются неименованные каналы => противоречие, поэтому укажу имена переменных для доступа к каналам: parent_to_child_fd и child_to_parent_fd) канала с помощью системного вызова pipe, а затем порождает дочерний процесс. После форка первый (родительский) процесс открывает и читает заданный файл, закрывает его и передает содержимое в parent_to_child_fd канал. Второй процесс принимает данные из parent_to_child_fd канала, обрабатывает их и передает результат вычислений в child_to_parent_fd канал. Первый процесс принимает массив из child_to_parent_fd канала, открывает файл для вывода и выполняет вывод в него, затем файл закрывает.  
  
#### О программе ####
Разработано консольное приложение в соответствии с заданием. Код в файле 6/6_task.c. Имена входного и выходного файлов задаются в качестве аргументов командной строки (./6_task input.txt output.txt). Чтение и запись в файлы происходит через системные вызовы read и write. Буфер для данных из файла и чтения из parent_to_child_fd канала имеет размер 5000. Для хранения результатов обработки используется целочисленный массив на 10 значений int.  
  
#### Тестрирование ####
В папке Tests представлен набор из 7 текстовых файлов, на которых проводилось тестирование. Для каждого теста в папке 6/Outputs представлен файл, полученный в результате работы программы.    
