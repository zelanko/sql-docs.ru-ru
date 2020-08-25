---
description: Грамматика формального формирования данных
title: Грамматика формальной фигуры | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 75cfedbafa7bc0c1b954f8bbdea29ec92d45c07f
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806828"
---
# <a name="formal-shape-grammar"></a>Грамматика формального формирования данных
Это формальное грамматика для создания любой команды Shape:  
  
-   Обязательные грамматические термины — это текстовые строки, разделенные угловыми скобками ("<>").  
  
-   Необязательные термины разделяются квадратными скобками ("[]").  
  
-   Альтернативы обозначаются виргуле ("&#124;").  
  
-   Повторяющиеся варианты обозначаются многоточием ("...").  
  
-   *Альфа* указывает строку алфавитных букв.  
  
-   *Цифра* указывает строку чисел.  
  
-   *Юникод-digit* указывает строку знаков Юникода.  
  
 Все остальные термины являются литералами.  
  
|Термин|Определение|  
|----------|----------------|  
|\<shape-command>|SHAPE [ \<table-exp> [как] \<alias> ]] [ \<shape-action> ]|  
|\<table-exp>|{ \<provider-command-text> } &#124;<br /><br /> ( \<shape-command> ) &#124;<br /><br /> Таблица \<quoted-name> &#124;<br /><br /> \<quoted-name>|  
|\<shape-action>|Добавление \<aliased-field-list> &#124;<br /><br /> ВЫЧИСЛЕНие \<aliased-field-list> [по \<field-list> ]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias> ]|  
|\<field-exp>|( \<relation-exp> ) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias> ]<br /><br /> ОТНОШЕНИЯ \<relation-cond-list>|  
|\<relation-cond-list>|\<relation-cond> [, \<relation-cond>...]|  
|\<relation-cond>|\<field-name> Кому \<child-ref>|  
|\<child-ref>|\<field-name> &#124;<br /><br /> ПАРАМЕТР \<param-ref>|  
|\<param-ref>|\<number>|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|SUM ( \<qualified-field-name> ) &#124;<br /><br /> AVG ( \<qualified-field-name> ) &#124;<br /><br /> MIN ( \<qualified-field-name> ) &#124;<br /><br /> MAX ( \<qualified-field-name> ) &#124;<br /><br /> COUNT ( \<qualified-alias> &#124; \<qualified-name> ) &#124;<br /><br /> STDEV ( \<qualified-field-name> ) &#124;<br /><br /> ANY ( \<qualified-field-name> )|  
|\<calculated-exp>|CALC ( \<expression> )|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<quoted-name>|  
|\<field-name>|\<quoted-name> [[AS] \<alias> ]|  
|\<quoted-name>|" \<string> " &#124;<br /><br /> " \<string> " &#124;<br /><br /> [ \<string> ] &#124;<br /><br /> \<name>|  
|\<qualified-name>|Псевдоним [. псевдоним...]|  
|\<name>|Alpha [альфа-&#124; цифра &#124; _ &#124; # &#124;: &#124;...]|  
|\<number>|цифра [цифра...]|  
|\<new-exp>|NEW \<field-type> [( \<number> [, \<number> ])]|  
|\<field-type>|Тип данных OLE DB или ADO.|  
|\<string>|Unicode-char [Юникод-char...]|  
|\<expression>|Visual Basic для приложений выражение, операнды которого являются другими столбцами, не являющимися ВЫЧИСЛЯЕМыми в одной строке.|  
  
## <a name="see-also"></a>См. также  
 [Доступ к строкам в иерархическом наборе записей](./accessing-rows-in-a-hierarchical-recordset.md)   
 [Общие сведения о формировании данных](./data-shaping-overview.md)   
 [Необходимые поставщики для формирования данных](./required-providers-for-data-shaping.md)   
 [Предложение APPEND для фигур](./shape-append-clause.md)   
 [Общие команды формы](./shape-commands-in-general.md)   
 [Предложение вычислений Shape](./shape-compute-clause.md)   
 [Функции Visual Basic для приложений](./visual-basic-for-applications-functions.md)