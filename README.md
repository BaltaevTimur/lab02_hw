# Балтаев Тимур ИУ8-22
## Part I
1) Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).


2) Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
```sh
$ git init
$ git remote add origin https://github.com/BaltaevTimur/lab02_hw.git
$ git pull origin main
$ touch REPORT.md
$ git add REPORT.md
$ git commit -m"added REPORT.md"
$ git push origin main
```
```sh
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 315 bytes | 315.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/BaltaevTimur/lab02_hw.git
   5bb77d4..3b2a26a  main -> main
```

3) Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.
```sh
$ alias edit=nano
$ cat > hello_world.cpp <<EOF
```
hello_world.cpp
```sh
#include <iostream>
using namespace std;

int main()
{
  cout << "Hello world!";
  return 0;
}
```

4) Добавьте этот файл в локальную копию репозитория.
```sh
$ git add hello_world.cpp 
```


5) Закоммитьте изменения с осмысленным сообщением.
```sh
$ git commit -m"adding hello_world.cpp"
$ git push origin main
```
```sh
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 378 bytes | 378.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/BaltaevTimur/lab02_hw.git
   3b2a26a..b3c12b4  main -> main
```

6) Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
```sh
$ edit hello_world.cpp
```


7) Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?
```sh
$ git commit -m"editing hello_world.cpp"
```
Файл не надо добавлять повторно, так как он уже есть.

8) Запуште изменения в удалёный репозиторий.
```sh
$ git push origin master
```
```sh
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 381 bytes | 381.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/BaltaevTimur/lab02_hw.git
   b3c12b4..d7c286e  main -> main
```

9) Проверьте, что история коммитов доступна в удалёный репозитории.
```sh
$ git log
```
```sh
commit d7c286e331f363e5447916a83e63999384480ee6 (HEAD -> main, origin/main)
Author: BaltaevTimur <timur.baltaev.2005@gmail.com>
Date:   Mon Mar 25 11:28:27 2024 +0300

    editing hello_world.cpp

commit b3c12b4ff6f9c43d96dafbc50af0908149592204
Author: BaltaevTimur <timur.baltaev.2005@gmail.com>
Date:   Mon Mar 25 11:24:04 2024 +0300

    adding hello_world.cpp

commit 3b2a26a00702a842d2b8c9e2024b37a773c039ee
Author: BaltaevTimur <timur.baltaev.2005@gmail.com>
Date:   Mon Mar 25 11:19:34 2024 +0300

    added REPORT.md

commit 5bb77d41cfa9c4a10770d7a3178ca84df07e0b2d
Author: BaltaevTimur <159756068+BaltaevTimur@users.noreply.github.com>
Date:   Mon Mar 25 11:09:15 2024 +0300

    Initial commit
lines 1-23
```
## Part II
1) В локальной копии репозитория создайте локальную ветку patch1.
```sh
$ git branch patch1
```


2) Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.
```sh
$ git switch patch1
$ edit hello_world.cpp
```
```sh
#include <iostream>
#include <string>


int main()
{
std::string name;
std::cin >> name;
std::cout << "Hello world from " << name;
return 0;
}
```


3) commit, push локальную ветку в удалённый репозиторий.
```sh
$ git commit -m"editting hello_world.cpp"
$ git push origin patch1
```
```sh
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 373 bytes | 373.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'patch1' on GitHub by visiting:
remote:      https://github.com/BaltaevTimur/lab02_hw/pull/new/patch1
remote: 
To https://github.com/BaltaevTimur/lab02_hw.git
 * [new branch]      patch1 -> patch1
```

4) Проверьте, что ветка patch1 доступна в удалёный репозитории.
```sh
$ git rebase patch1
```
Current branch patch1 is up to date.


6) В локальной копии в ветке patch1 добавьте в исходный код комментарии.
```sh
$ edit hello_world.cpp
```
```sh
#include <iostream>
#include <string>


int main()
{
std::string name; // создаем переменную
std::cin >> name; // вводим значение
std::cout << "Hello world from " << name; // выводим
return 0;
}
```

7) commit, push.
```sh
$ git commit -m"editting hello_world.cpp"
$ git push origin patch1
```
```sh
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 440 bytes | 440.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/BaltaevTimur/lab02_hw.git
   b07d324..3a28002  patch1 -> patch1
```

8) Проверьте, что новые изменения есть в созданном на шаге 5 pull-request
```sh
$ git rebase patch1
```
Current branch patch1 is up to date.

9) В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.
```sh
$ git merge patch1
```
```sh
Updating 209fb86..c020edc
Fast-forward
hello_world.cpp | 8 ++++----
1 file changed, 4 insertions(+), 4 deletions(-)
```


10) Локально выполните pull.
```sh
$ git pull origin patch1
```
```sh
From https://github.com/BaltaevTimur/lab02_hw
 * branch            patch1     -> FETCH_HEAD
Already up to date.
```

11) С помощью команды git log просмотрите историю в локальной версии ветки master.
```sh
$ git log
```
```sh
commit 3a28002114532a6647b47c6679c96827a9a6999c (HEAD -> patch1, origin/patch1)
Author: BaltaevTimur <timur.baltaev.2005@gmail.com>
Date:   Tue Mar 26 04:15:35 2024 +0300

    editting hello_world.cpp

commit b07d32415c8b36c28c53879f5c91033129ae15bf (main)
Author: BaltaevTimur <timur.baltaev.2005@gmail.com>
Date:   Mon Mar 25 11:39:05 2024 +0300

    editting hello_world.cpp

commit d7c286e331f363e5447916a83e63999384480ee6
Author: BaltaevTimur <timur.baltaev.2005@gmail.com>
Date:   Mon Mar 25 11:28:27 2024 +0300

    editing hello_world.cpp

commit b3c12b4ff6f9c43d96dafbc50af0908149592204
Author: BaltaevTimur <timur.baltaev.2005@gmail.com>
Date:   Mon Mar 25 11:24:04 2024 +0300

lines 1-22
```

12) Удалите локальную ветку patch1.
```sh
$ git branch -d patch1
```
Deleted branch patch1 (was 3a28002).

## Part III

1) Создайте новую локальную ветку patch2.
```sh
$ git branch patch2
```


3) commit, push, создайте pull-request patch2 -> master.
```sh
$ git commit -m"editting hello_world.cpp"
$ git push origin patch2
```


5) Убедитесь, что в pull-request появились конфликтны.

Появились конфликты.


6) Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.

```sh
$ git pull --rebase origin main
```
```sh
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 6 (delta 3), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), 3.51 KiB | 359.00 KiB/s, done.
From https://github.com/BaltaevTimur/lab02_hw
 * branch            main       -> FETCH_HEAD
   1687254..f4bd38c  main       -> origin/main
Updating b07d324..f4bd38c
Fast-forward
 README.md       | 304 +++++++++++++++++++++++++++++++++++++++++++++++++++++++-
 hello_world.cpp |   8 +-
 2 files changed, 307 insertions(+), 5 deletions(-)
```

8) Убедитель, что в pull-request пропали конфликтны.

Пропали.


