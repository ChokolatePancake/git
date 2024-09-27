# git
git checkout -b test (створення нової гілки)
git add .(додає зміни до індексу)
git status(виводить різницю між індексом і робочою текою)
git commit -m"test"(створення нового коміту)
git push --set-upstream origin test(відправлення на віддалений сервер)

git checkout main(переключення на гілку)
git revert створює новий коміт з протилежними змінами до поточного(якщо щось видалено, то буде додано, якщо додано, то видалено)

git reset має кілька варіацій: mixed(default), soft, hard. 
Soft залишає всі зміни в індексі і в будь-який момент можна створити новий коміт(наприклад було кілька комітів, але зараз їх треба об'єднати в один). 
Mixed(за замовчуванням) видаляє зміни з індексу, але лишає в робочій теці(наприклад було закомічено зайвий файл, при такому ресеті треба буде знову використовувати git add, тож можна переглянути ще раз які зміни справді хочем внести).
Hard повністю видаляє коміти з їх змінами усюди

git rebase дає можливість перенести коміти з однієї гілки на іншу
git cherry-pick дає можливість перенести кілька конкретних комітів

git commit --amend(дозволяє змінити останній коміт зберігаючи чистоту історії комітів, корисне коли треба змінити повідомлення коміту, або щось забули змінити в файлах(треба прописати git add перед тим як запускати в такому випадку). Якщо ввести в такому вигляді як є, то відкриє текстовий редактор, де можна змінити назву)
Варто використовувати на ще не запушених комітах(інакше доведеться застосувати git push --force), при значних змінах краще створювати новий коміт, щоб не заплутувати історію
Додаткові опції:
*-m"some text"(для зміни повідомлення не заходячи в редактор)
*--no-edit(для зміни лише наповнення коміта, без зміни повідомлення)
*--edit(дефолтна опція, що відкриває текстовий редактор для редагування повідомлення)
*--reset-author(для зміни автора коміту)
*--no-verify(ігнорує попередньо налаштовані перевірки)
*--date="some date"(для задання нової дати коміту)
*--author="author <author@example.com>"(для задання нового автора та електронки)

git reset --hard ORIG_HEAD (перша частина примусово повертає гілку до вказаного коміту, а саме ORIG_HEAD)
ORIG_HEAD - точка повернення до останньої великої операції(merge, rebase, reset, pull)
