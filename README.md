# Развёртывание проекта Laravel для Веб-хостинга | For true dev
***
### Настройка локального окружения <br> <br>(OsPanel, GitBash, Composer)
<h3>1. Установка OpenServer</h3>
Не стал ставить все компоненты, поставил только нужные для развёртывания Laravel'a. 
Можете выполнять стандартную установку со всеми предлагаемымми компонентами. </p> 
<p>У меня вышло чёт такое:</p>

![img.png](images-for-git/img.png) <br>

![img_1.png](images-for-git/img_1.png) <br>

<h4>Для развёртывания Laravel хватит и этих модулей:</h4>
1. HTTP: Apache_2.4PHP_8.0 (есть вариация с NGINX, но её лучше не использовать иначе нужно будет беседовать с composer'om)
2. Php: PHP_8.0




![img_2.png](images-for-git/img_2.png) <br>

<p><b>Сохранить и перезагрузить OSPanel</b></p>
<h3>2. Установка Git'a</h3>

<p>Можете выбрать редактор кода, который больше нравится вам или оставить поумолчанию. В моём предпочтении VsCode</p>

<p>Остальные настройки по умолчанию</p>

![img_6.png](images-for-git/img_6.png) <br>

<h3>3. Установка Composer'a</h3>
<p>Да, он вроде шёл вместе с OSPanel, но привычка, и так действительно лучше) </p>
<p>Прокладываете путь к модулю пыхи в OsPanel Остальное по умолчанию</p>

![img_22.png](images-for-git/img_22.png) <br>

<p>Для проверки что всё установлено правильно, можете зайти в gitBash и прописать:</p><code>composer --version</code>


![img_23.png](images-for-git/img_23.png) <br>


***

<h2>Развёртывание проекта Laravel на локальной машине</h2>
1. Стартуем OsPanel;
2. Открываем GitBash (можно просто ввести в меню пуск git скорее всего git bash будет первым в списке);
3. В GitBash'e переходим в директорию <code>OpenServer\domains</code> у меня это <code>C:\OpenServer\domains</code> для этого в bash'e нужно написать следующее <br> <code>cd /C/OpenServer/domains/
   </code> <br>

   ![img_20.png](images-for-git/img_20.png) <br>

4. Качаем проект через <b>composer</b>. Для этого в bash вводим: <br> <code>composer create-project laravel/laravel</code> <br>
   ![img_21.png](images-for-git/img_21.png) <br>
   <br>
   ![img_24.png](images-for-git/img_24.png) <br>
   <br>
   ![img_25.png](images-for-git/img_25.png) <br>

5. После автоматической установки всех пакет и обновления всех зависимостей. Переходим в папке проекта. GitBash: <br> 
<code>cd laravel</code> <br>

   ![img_26.png](images-for-git/img_26.png) <br>

6. Проверяем, что проект работает запуская его: <br> 
<code>php artisan serve</code>
   ![img_27.png](images-for-git/img_27.png) <br>
7. В браузере переходим по адресу: <code>http://127.0.0.1:8000 </code>
    <p>Если всё ОК, то видим следующее</p>

    ![img_28.png](images-for-git/img_28.png) <br>

<h2>Подготовка проекта к отправке на хостинг</h2>
1. <p>Чтобы вернуть возможность писать команды в Bash'e и выключить сервер используем сочетание клавиш: <code>CTRL + C</code> </p>
2. <p>В директории <code>domains\laravel</code> ищем два файла <code>composer.json</code> и <code>composer.lock</code> открываем их любом текстовом редакторе.</p> 
3. <p>В файле <code>composer.json</code> редактируем строчку № 8, <code>"php": "^7.3|^8.0"</code> в итоге должно получиться <code>"php": "^7.3"</code>, сохраняем файл </p>
4. <p>В файле <code>composer.lock</code> редактируем строчку № 24, <br><code>"php": "^7.0|^8.0"</code> в итоге должно получиться <code>"php": "^7.0"</code>, сохраняем файл</p>
5. В Bash'e вводим <code>composer install --ignore-platform-reqs</code>
    ![img_29.png](images-for-git/img_29.png) <br>
6. Получаем сообщение:
    ![img_30.png](images-for-git/img_30.png) <br>
7. Можно закрыть Bash.
8. Архивируем папку Laravel.

<h2>Подготовка хостинга для загрузки проекта</h2>
1. Переходим в админ панель хостинга под своими данными.
2. Заходим во вкладку "Sites"
![img_31.png](images-for-git/img_31.png) <br>
3. Нажимаем на шестерёнку в форме "Sites and linked domains" 
![img_32.png](images-for-git/img_32.png) <br>
4. Меняем версию php с 5.6 на 7.4
    ![img_33.png](images-for-git/img_33.png) <br>
    ![img_34.png](images-for-git/img_34.png) <br>
5. Возвращаемся на главную страницу админки
6. Переходим на вкладку "File manager" 
    ![img_35.png](images-for-git/img_35.png) <br>
7. После того как перешли в Файловый менеджер заходим в папку с сайтом у меня это <code>e92507ja.beget.tech</code>
    ![img_36.png](images-for-git/img_36.png) <br>
8. В папку с сайтом <code>e92507ja.beget.tech</code> грузим наш проект архивом <code>laravel.7z[.rar, .zip]</code>
<p>Для этого в менюшке сверху выбираем "Загрузить файлы"</p>

![img_37.png](images-for-git/img_37.png) <br>

<p>Дальше жмём <b>Browse...</b> и выбираем архив и жмём "Открыть" потом в форме нажимаем "Загрузка" </p>

![img_38.png](images-for-git/img_38.png) <br>
     
![img_39.png](images-for-git/img_39.png) <br>

<p>После того как файл был загружен можем закрыть форму</p>

![img_40.png](images-for-git/img_40.png) <br>

<p>Жмём по архиву "ПКМ" - "Распаковать архив" </p>

![img_41.png](images-for-git/img_41.png) <br>

<p>Распаковка займёт какое-то время. </p>

<p>Спустя 5-8 мин. Архив распакован. <br> 
В итоге в папке <code>e92507ja.beget.tech</code> у нас находятся 3 файла: папка <code>laravel</code>, папка <code>public_html</code>, архив <code>laravel.7z</code></p>

![img_42.png](images-for-git/img_42.png) <br>

9. <p>В левом окне открываем папку <code>laravel</code>, а вправом папку <code>public_html</code> и в правом окне удаляем все файлы кроме папки <br> <code>cgi-bin</code> в итоге должно выглядить как на скриншоте ниже</p>
   
![img_43.png](images-for-git/img_43.png) <br>
10. <p>В левом окне переходим в папку <code>public</code>, выделяем все файлы кроме <code>..</code>, далее жмём "ПКМ" - "Переместить"<p>

![img_44.png](images-for-git/img_44.png) <br>

11. <p>В итоге, все файлы из папки <code>public</code> переместились в папку <code>public_html</code></p>
![img_45.png](images-for-git/img_45.png) <br>

12. <p>В папке <code>public_html</code> открываем файл <code>index.php</code> чтобы отредактировать его <br> Нас интересует строка № 34 <br> <code>require __DIR__.'/../vendor/autoload.php';</code></p> 
<p>Перед <code>vendor</code> добавляем директорию <code>laravel</code></p>

<p>В итоге строка должна выглядить так: <br><code>require __DIR__.'/../laravel/vendor/autoload.php';</code></p>
<p>Дальше в этом же файле ищем строку №47: <br> <code>$app = require_once __DIR__.'/../bootstrap/app.php';</code></p>
<p>Делаем тоже самое. В итоге строка выглядит, так: <br> <code>$app = require_once __DIR__.'/../laravel/bootstrap/app.php';</code></p>

![img_46.png](images-for-git/img_46.png) <br>

<p>Сохраняем файл. "Файл" - "Сохранить". <br> Можем переходить на главную страницу сайта у меня: <code>http://e92507ja.beget.tech/</code></p>

<p>Если всё сделано верно, увидим экран приветствия Laravel:</p>

![img_47.png](images-for-git/img_47.png) <br>

***

# Развёртывание проекта Laravel для Веб-хостинга | For not true dev
1. Клонировать репозиторий в любую папку: <br>
<code>git clone https://github.com/Vampir007one/UploadLaravelToHosting.git </code>
2. Загрузить архив на хостинг, распаковать в корне сайта рядом с папкой <code>public-html</code>. 
3. Удалить все файлы в папке <code>public_html</code> кроме папки <code>cgi-bin</code>.
4. Из папки <code>laravel\public</code> переместить всё в папку <code>public_html</code>
5. Перейти на главую страницу сайта. Всё должно работать
