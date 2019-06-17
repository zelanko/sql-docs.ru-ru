---
title: Грамматика формального формирования | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0af2421a0d1f80922560be556062c89074c21838
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701997"
---
# <a name="formal-shape-grammar"></a>Грамматика формального формирования данных
Это формальная Грамматика для создания любой фигуры команд:  
  
-   Необходимые условия грамматических являются текстовыми строками, угловые скобки («<>»).  
  
-   Необязательные условия разделены с помощью квадратных скобок («[]»).  
  
-   Альтернативные варианты указаны косая черта (»&#124;«).  
  
-   Повторяющийся альтернативные варианты указаны многоточие («...»).  
  
-   *Альфа-канал* указывает строку буквы алфавита.  
  
-   *Цифра* указывает из числовых строк.  
  
-   *Юникод значный* указывает строки знаков Юникода.  
  
 Все другие условия являются литералами.  
  
|Термин|Определение|  
|----------|----------------|  
|\<Команда фигуры >|ФИГУРЫ [\<exp таблицы > [[AS] \<псевдоним >]] [\<действие фигуры >]|  
|\<table-exp>|{\<provider-command-text>} &#124;<br /><br /> (\<фигуры command >)&#124;<br /><br /> Таблица \<заключено в кавычки name >&#124;<br /><br /> \<заключенный в кавычки name >|  
|\<Фигура действия >|ДОБАВЛЕНИЕ \<псевдоним поле list >&#124;<br /><br /> ВЫЧИСЛЕНИЯ \<псевдоним поле list > [BY \<список полей >]|  
|\<aliased-field-list>|\<псевдоним поля > [, \<псевдоним поля... >]|  
|\<aliased-field>|\<поле exp > [[AS] \<псевдоним >]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<exp таблицы > [[AS] \<псевдоним >]<br /><br /> ССЫЛКА \<отношения cond-list >|  
|\<связь cond-list >|\<отношение cond > [, \<отношения cond >...]|  
|\<отношение cond >|\<Имя поля > TO \<дочерних ref >|  
|\<дочерний ref >|\<Имя поля >&#124;<br /><br /> ПАРАМЕТР \<param ref >|  
|\<PARAM ref >|\<Номер >|  
|\<field-list>|\<Имя поля > [, \<имя поля >]|  
|\<aggregate-exp>|SUM(\<qualified-field-name>) &#124;<br /><br /> AVG(\<qualified-field-name>) &#124;<br /><br /> MIN(\<qualified-field-name>) &#124;<br /><br /> MAX(\<qualified-field-name>) &#124;<br /><br /> COUNT(\<qualified-alias> &#124; \<qualified-name>) &#124;<br /><br /> STDEV (\<полное поле имя->)&#124;<br /><br /> ЛЮБОЙ (\<полное поле имя->)|  
|\<вычисляется exp >|Калькулятор (\<выражение >)|  
|\<Полное поле имя->|\<alias>.[\<alias>...]\<field-name>|  
|\<псевдоним >|\<заключенный в кавычки name >|  
|\<Имя поля >|\<заключенный в кавычки имя > [[AS] \<псевдоним >]|  
|\<заключенный в кавычки name >|"\<string>" &#124;<br /><br /> '\<string>' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<Имя >|  
|\<Полное имя >|псевдоним [.alias]|  
|\<Имя >|alpha [ alpha &#124; digit &#124; _ &#124; # &#124; : &#124; ...]|  
|\<Номер >|цифра [цифра...]|  
|\<new-exp>|НОВЫЙ \<тип поля > [(\<номер > [, \<номер >])]|  
|\<Тип поля >|Тип данных OLE DB или ADO.|  
|\<строка >|Юникод char [Юникода char...]|  
|\<expression>|Visual Basic для приложений выражения, операнды которых являются другие столбцы не CALC в той же строке.|  
  
## <a name="see-also"></a>См. также  
 [Доступ к строкам в иерархических наборах записей](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Общие сведения о формировании данных](../../../ado/guide/data/data-shaping-overview.md)   
 [Обязательные поставщики для формирования данных](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Предложение APPEND для формирования](../../../ado/guide/data/shape-append-clause.md)   
 [Общие сведения о командах фигуры](../../../ado/guide/data/shape-commands-in-general.md)   
 [Предложение COMPUTE для формирования](../../../ado/guide/data/shape-compute-clause.md)   
 [Функции Visual Basic для приложений](../../../ado/guide/data/visual-basic-for-applications-functions.md)
