postgres зберігає дані у файлах, які розділені в сегменти по 8кб, коли ми запитуємо якись рядок, postgres в будь якому разі зчитає також і інші рядки в цьому сегменті. Прочитані сегменти зберігаються в буферній памяті (ОЗП). Краще розбивати дані по різним таблицям щоб в одному сегменті було якнайбільше рядків.