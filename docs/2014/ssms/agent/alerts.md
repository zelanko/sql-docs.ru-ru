---
title: Предупреждения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, event types
- SQL Server Agent alerts, names
- alerts [SQL Server], performance conditions
- alerts [SQL Server], about alerts
- WMI event responses [SQL Server Agent alerts]
- events [WMI]
- performance condition alerts [SQL Server Agent]
- alerts [SQL Server], event types
- SQL Server Agent alerts, performance conditions
- SQL Server Agent alerts, about alerts
- alerts [SQL Server], names
ms.assetid: 3f57d0f0-4781-46ec-82cd-b751dc5affef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 946bfd0c05e7739af4bfebf799980a0dc27de245
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065016"
---
# <a name="alerts"></a>видны узлы
  События, формируемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , помещаются в журнал приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент считывает этот журнал и сравнивает события, которые там содержатся, с определенными пользователем предупреждениями. Как только агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаруживает такое соответствие, в ответ на это событие автоматически создается предупреждение. Кроме событий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может отслеживать условия производительности и события инструментария управления Windows (WMI).  
  
 Чтобы определить предупреждение, необходимо указать:  
  
-   Имя предупреждения.  
  
-   событие или условие производительности, по которому создается это предупреждение;  
  
-   действие, которое агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предпринимает по этому событию или условию производительности.  
  
## <a name="naming-an-alert"></a>Имена предупреждений  
 У каждого предупреждения должно быть имя. Имена предупреждений должны быть уникальны в пределах экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не могут иметь длину более **128** символов.  
  
## <a name="selecting-an-event-type"></a>Выбор типа события  
 Предупреждение создается в ответ на событие определенного типа. В частности, на следующие типы события:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] события;  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] условия производительности;  
  
-   события инструментария WMI  
  
 Тип события определяет параметры, которые указываются для точного определения события.  
  
## <a name="specifying-a-sql-server-event"></a>Указание события SQL Server  
 Можно определить, чтобы предупреждение создавалось в ответ на одно или несколько событий. Для указания событий, по которым создается предупреждение, используются следующие параметры.  
  
-   **Номер ошибки**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент создает предупреждение при возникновении определенной ошибки. Например, можно указать код ошибки 2571 для отслеживания попыток неавторизованного обращения к консольным командам базы данных (DBCC).  
  
-   **Степень серьезности**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент создает предупреждение при возникновении любой ошибки определенного уровня серьезности. Например, можно указать уровень серьезности 15 для обработки ошибок синтаксиса в инструкциях на языке Transact-SQL.  
  
-   **База данных**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент создает предупреждение, когда событие возникает в определенной базе данных. Этот параметр применяется в дополнение к коду или уровню серьезности ошибки. Например, если экземпляр содержит производственную базу данных и базу данных для отчетности, можно определить предупреждение, которое будет создаваться только при синтаксических ошибках, возникающих в производственной базе данных.  
  
-   **Текст события**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент создает предупреждение, если в сообщении о событии содержится определенная текстовая строка. Например, можно определить предупреждение, которое будет создаваться для сообщений, содержащих имя определенной таблицы или ограничения.  
  
## <a name="selecting-a-performance-condition"></a>Выбор условия производительности  
 Можно определить, чтобы предупреждение создавалось в ответ на определенное условие производительности. В этом случае указывается отслеживаемый счетчик производительности, порог предупреждения и действие, по которому предупреждение создается. Чтобы назначить условие производительности, необходимо определить в агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значения следующих элементов на странице **Общие** диалогового окна **Создание предупреждения** или **Свойства предупреждения** :  
  
-   **Объект**  
  
     Объект — область отслеживания производительности.  
  
-   **Счетчик**  
  
     Счетчик — атрибут отслеживаемой области.  
  
-   **Экземпляр**  
  
     Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет конкретный экземпляр (если есть) отслеживаемого атрибута.  
  
-   **Создать предупреждение, если счетчик:** и **Значение**  
  
     Пороговое значение и действие, по которому срабатывает предупреждение. Пороговое значение — число. Действие — **одно из следующих значений: меньше**, **равно**или **больше по отношению к значению, указанному в поле "Значение"**. **Значение** — числовое значение счетчика условия производительности. Например, чтобы определить срабатывание предупреждения для объекта производительности **SQLServer:Locks** , если значение **Время ожидания блокировки** превышает 30 минут, необходимо выбрать **больше** и **указать 30 в поле значения**.  
  
     Или, например, можно указать, что предупреждение срабатывает для объекта производительности **SQLServer:Transactions** , когда свободное место в базе данных **tempdb** становится меньше 1000 КБ. Для этого выберите счетчик **Свободное пространство в tempdb (КБ)**, **меньше**и введите **1000** в поле **Значение**.  
  
    > [!NOTE]  
    >  Сведения о производительности снимаются не в реальном времени, что может привести к небольшой задержке (в несколько секунд) между достижением порогового значения и срабатыванием предупреждения условия производительности.  
  
## <a name="selecting-a-wmi-event"></a>Выбор события инструментария WMI  
 Можно указать, чтобы предупреждение создавалось в ответ на определенное событие инструментария WMI. Чтобы назначить событие инструментария WMI, необходимо определить в агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следующие элементы на странице **Общие** диалогового окна **Создание предупреждения** или **Свойства предупреждения** :  
  
-   **Пространство имен**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент регистрируется в качестве клиента WMI в пространстве имен инструментария WMI, выделенном для запроса событий.  
  
-   **Запрос**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент для определения конкретного события пользуется инструкцией на языке запросов инструментария управления Windows (WQL).  
  
 Ниже приведены ссылки на часто выполняемые задачи.  
  
 **Создание предупреждения по номеру сообщения**  
  
-   [Среда SQL Server Management Studio](create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **Создание предупреждения по уровню серьезности**  
  
-   [Среда SQL Server Management Studio](create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **Создание предупреждения по событию инструментария WMI**  
  
-   [Среда SQL Server Management Studio](create-a-wmi-event-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **Определение ответа на предупреждение**  
  
-   [Среда SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 **Создание сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 **Изменение сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 **Удаление сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 **Отключение или повторное включение предупреждения**  
  
-   [Среда SQL Server Management Studio](disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Использование объектов SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md)  
  
  
