# Git

- `git checkout -b` (створення нової гілки)
- `git add .` (додає зміни до індексу)
- `git status` (виводить різницю між індексом і робочою текою)
- `git commit -m "test"` (створення нового коміту)
- `git push --set-upstream origin test` (відправлення на віддалений сервер)

- `git checkout` (переключення на гілку)
- `git revert` створює новий коміт з протилежними змінами до поточного (якщо щось видалено, то буде додано, якщо додано, то буде видалено)

`git reset` має кілька варіацій: mixed (default), soft, hard.
- Soft залишає всі зміни в індексі і в будь-який момент можна створити новий коміт (наприклад було кілька комітів, але їх треба об'єднати в один)
- Mixed (за замовчуванням) видаляє зміни з індексу, але лишає в робочій теці (наприклад було закомічено зайвий файл, після ресету можна додати потрібні файли і закомітити)
- Hard повністю видаляє коміти з їх змінами усюди

------------------------------------------------------------------------------
- `git rebase` дає можливість перенести коміти з однієї гілки на іншу
- `git cherry-pick` дає можливість перенести один або кілька конкретних комітів

`git commit --amend` (дозволяє змінити останній коміт зберігаючи чистоту історії комітів, корисне коли треба змінити повідомлення або щось додати)
Варто використовувати на ще не запушених комітах (інакше доведеться застосувати git push --force), при значних змінах краще створити новий коміт
Додаткові опції:
- `-m "some text"` (для зміни повідомлення не заходячи в редактор)
- `--no-edit` (для зміни лише наповнення коміта, без зміни повідомлення)
- `--edit` (дефолтна опція, що відкриває текстовий редактор для редагування повідомлення)
- `--reset-author` (для зміни автора коміту)
- `--no-verify` (ігнорує попередньо налаштовані перевірки)
- `--date="some date"` (для задання нової дати коміту)
- `--author="author <author@example.com>"` (для задання нового автора та електронки)

`git reset --hard ORIG_HEAD` (перша частина примусово повертає гілку до вказаного коміту, а саме ORIG_HEAD)
ORIG_HEAD - точка повернення до останньої великої операції (merge, rebase, reset, pull)

`git log` (відображає коміти на поточній гілці)

`git reflog` (показує усі зміни, в тому числі коміти, які вже є недоступними через зміни в гілках або скидання, також показує усі операції з гілками)

`git tag "tag name"` (дозволяє створювати теги на конкретний коміт)
Додаткові опції:
- `-l` (без вказування "tag name", виводить список усіх тегів, можна фільтрувати наприклад "a*" виведе усі теги, що починаються на "a")
- `-a` (анотований тег, якщо окрім самої назви тега треба додаткова інформація, після -a пишеться власне назва)
- `-m` (повідомлення анотованого тегу)
- `-f` (force, примусове переписування тегу)
- `-d` (delete, видалення тегу)
- `--contains <commit>` (показує теги, які містить вказаний коміт)
- `--points-at <object>` (показує теги, які вказують на об'єкт (коміт, гілку))
- `--edit` (дозволяє відредагувати існуючий анотований тег)

`git fetch` (підтягує зміни з віддаленого репозиторію до локального, але не об'єднує їх)

`git pull` (підтягує зміни та зливає з локальною гілкою)

`git stash` (дозволяє зберегти незакомічені зміни локально, при цьому наче вирізаючи їх. Коли на гілці є зміни, які не готові ще до коміту, але необхідно перейти на іншу гілку, stash вертає теку в стан останнього коміту, а сам зберігає усі зміни, тож завжди можне вернутися до того, на чому зупинився. Зміни зберігаються стеком десь в папці .git/objects)


`git stash pop`(відновлює зміни, вирізаючи їх зі стеку)

`git stash apply`(відновлює зміни, але також залишає їх в стеку)

`git stash list`(для перегляду усіх прихованих змін)

`git stash push -m "some text"`(зберігає в стек з вказаним повідомленням)

`git stash show`(показує зміни в останньому записі стешу)

`git stash drop`(видаляє або останній, або вказаний запис стешу)

`git stash clear`(видаляє всі записи стешу)


