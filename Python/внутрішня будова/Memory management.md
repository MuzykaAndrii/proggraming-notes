Після видалення об'єкту з пам'яті [[Garbage collector|garbage collector'ом]] в пулі пам'яті, який Python запросив у операційної системи, цей фрагмент пам'яті зберігається зарезервованим для того щоб в разі необхідності покласти туди інший об'єкт із таким ж розміром. Таким чином Python економить ресурси і не робить повторний запит на виділення пам'яті в операційної системи.

[[Внутрішня будова]]