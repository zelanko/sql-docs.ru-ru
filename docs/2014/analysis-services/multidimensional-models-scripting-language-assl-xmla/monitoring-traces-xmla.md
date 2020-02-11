---
title: Мониторинг трассировок (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, traces
- XMLA, traces
- monitoring traces [XMLA]
- traces [Analysis Services]
ms.assetid: cdbfb984-18bd-4c4e-8fb7-d64ce298ed35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 678c6d2312261475f4b970b1535ce1faa1f00930
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62729078"
---
# <a name="monitoring-traces-xmla"></a>Наблюдение за трассировками (XMLA)
  С помощью команды [Subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) в XML для АНАЛИТИКИ (XMLA) можно отслеживать существующую трассировку, определенную в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]служб. Команда `Subscribe` возвращает результаты трассировки в виде набора строк.  
  
## <a name="specifying-a-trace"></a>Задание трассировки  
 Свойство [объекта](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) `Subscribe` команды должно содержать ссылку на объект либо на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр, либо на трассировку в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляре. Если свойство `Object` не задано или в свойстве `Object` не указан идентификатор трассировки, команда `Subscribe` отслеживает трассировку сеанса по умолчанию для явного сеанса, указанного в заголовке SOAP для данной команды.  
  
## <a name="returning-results"></a>Возвращаемые результаты  
 Команда `Subscribe` возвращает набор строк, содержащий события трассировки, которые зафиксировала указанная трассировка. `Subscribe` Команда возвращает результаты трассировки до отмены команды командой [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) .  
  
 Набор строк содержит столбцы, перечисленные в следующей таблице.  
  
|Столбец|Тип данных|Description|  
|------------|---------------|-----------------|  
|EventClass|Целое число|Класс события, полученного трассировкой.|  
|EventSubclass|Long integer|Подкласс события, полученного трассировкой.|  
|CurrentTime|Datetime|Время начала события, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|StartTime|Datetime|Время начала события, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|EndTime|Datetime|Время окончания события, если оно известно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».<br /><br /> Этот столбец не заполняется для классов событий, описывающих начало процесса или действия.|  
|Duration|Long integer|Общее время (в миллисекундах), прошедшее для события.|  
|CPUTime|Long integer|Общее время процессора (в миллисекундах), прошедшее для события.|  
|JobID|Long integer|Идентификатор задания для процесса.|  
|SessionID|String|Идентификатор сеанса, к которому относится происшедшее событие.|  
|SessionType|String|Тип сеанса, к которому относится происшедшее событие.|  
|ProgressTotal|Long integer|Общий ход выполнения, о котором сообщает событие, в числовом или количественном выражении.|  
|IntegerData|Long integer|Целочисленные данные, связанные с событием. Содержимое этого столбца зависит от класса событий и подкласса событий.|  
|ObjectID|String|Идентификатор объекта, к которому относится происшедшее событие.|  
|ObjectType|String|Тип объекта, указанного в ObjectName.|  
|ObjectName|String|Имя объекта, к которому относится происшедшее событие.|  
|ObjectPath|String|Иерархический путь объекта, к которому относится происшедшее событие. Путь представлен в виде строки идентификаторов объектов, разделенной запятыми, для родителей объекта, указанного в ObjectName.|  
|ObjectReference|String|XML-представление ссылки объекта для объекта, указанного в ObjectName.|  
|NestLevel|Целое число|Уровень транзакции, к которой относится происшедшее событие.|  
|NumSegments|Long integer|Количество сегментов данных, затронутых или открытых командой, к которой относится происшедшее событие.|  
|Severity|Целое число|Степень серьезности исключения для события. Столбец может содержать одно из следующих значений.<br /><br /> Значение: 0 = успешное завершение<br /><br /> Значение: 1 = сведения<br /><br /> Значение: 2 = предупреждение<br /><br /> Значение: 3 = ошибка|  
|Успех|Логическое|Указывает, выполнена ли команда успешно или окончилась неудачей.|  
|Ошибка|Long integer|Номер ошибки события, если это применимо.|  
|ConnectionID|String|Идентификатор соединения, к которому относится происшедшее событие.|  
|имя_базы_данных|String|Имя базы данных, к которой относится происшедшее событие.|  
|NTUserName|String|Имя пользователя Windows, связанного с событием.|  
|NTDomainName|String|Домен пользователя Windows, связанного с событием.|  
|ClientHostName|String|Имя компьютера, на котором выполняется клиентская программа. Данный столбец заполняется значениями, переданными клиентским приложением.|  
|ClientProcessID|Long integer|Идентификатор процесса клиентского приложения.|  
|ApplicationName|String|Имя клиентского приложения, установившего соединение с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми клиентским приложением, а не отображаемым именем программы.|  
|NTCanonicalUserName|String|Каноническое имя пользователя Windows пользователя, связанного с событием.|  
|SPID|String|Идентификатор процесса сервера (SPID) сеанса, к которому относится происшедшее событие. Значение этого столбца непосредственно соответствует идентификатору сеанса, указанному в заголовке SOAP сообщения XMLA, к которому относится происшедшее событие.|  
|TextData|String|Текстовые данные, связанные с событием. Содержимое этого столбца зависит от класса событий и подкласса событий.|  
|имя_сервера;|String|Имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], к которому относится происшедшее событие.|  
|RequestParameters|String|Параметры параметризированного запроса или команды XMLA, к которой относится происшедшее событие.|  
|RequestProperties|String|Свойства метода XMLA, к которому относится происшедшее событие.|  
  
## <a name="see-also"></a>См. также:  
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
