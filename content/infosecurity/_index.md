---
type : docs
---
> Кто владеет информацией, тот владеет миром[^1] 

Информационная безопасность это обеспечение [конфиденциальности, целостности и доступности](introduction) защищаемой информации. Все просто, но "дьявол кроется в деталях" и под этой простотой скрывается много математики, техники и юриспруденции.

## Думай как преступник
Сложность системы зависит от количества составляющих и связей между ними. Защищенность системы равна защищенности самого слабого её компонента. С ростом сложности системы растет вероятность появления - и обнаружения! - в ней слабых мест. 

Исследование на уязвимости -- это выявление способов, которыми информацию можно скомпрометировать, нарушить или сделать недоступной. От компьютерных преступлений это отличается лишь мотивами. В конце концов, замки ломают не только преступники, но и спасатели. Так и здесь – есть «белые» хакеры[^2] и «черные». 

[Этичный взлом](pentest) подразумевает, что операции по выявлению уязвимости проводятся с согласия владельцев информационных систем, полученная информация будет передана им же и в других целях использована не будет.

## Думай как стражник
Технические средства защиты информации закрывают лазейки для хакеров. Правильным, конечно, является создание изначально защищенных и надежных систем, но это утопия. Особенно, когда разнородные подсистемы являются частью другой, более глобальной. Так что системы защиты информации все равно нужны - и [разграничение доступа](access_restriction), и [обнаружение и предотвращение атак](IDS-IPS), и [мониторинг аномалий](SIEM). А еще [управление уязвимостями] для создания [эшелонированной защиты].

## Думай как политик
В реальном мире нет идеальных систем и абсолютной защиты. Зато в нем есть [законы, предписания, требования](documentary) и их необходимо соблюдать. Но не только. "Политический" уровень информационной безопасности это еще и [организационные меры] и [управление_рисками]. 

Кроме того, помимо вопроса "что делать?" всегда есть вопрос "кто виноват?". Все изменения в системах и предоставление доступов должно иметь документальное, юридически значимое обоснование. Для этого используется та или иная [система электронного документооборота] с заявками, согласованиями и ответственными. В качестве бонуса такая система может дополнять - или даже полностью подменять - специализированные [системы контроля изменений].

[^1]: Натан Майер Ротшильд
[^2]: Тонкости определения слова "хакер" оставим соответствующей субкультуре, а мы будем использовать это слово в значении "взломщик"