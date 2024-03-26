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
##Part II
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

5) Создайте pull-request patch1 -> master.

[pull_request](https://github.com/BaltaevTimur/lab02_hw/pull/1)

5) В локальной копии в ветке patch1 добавьте в исходный код комментарии.
```sh
```


7) commit, push.
```sh
```


8) Проверьте, что новые изменения есть в созданном на шаге 5 pull-request
```sh
```


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
```


11) С помощью команды git log просмотрите историю в локальной версии ветки master.
```sh
```


12) Удалите локальную ветку patch1.
```sh
```


