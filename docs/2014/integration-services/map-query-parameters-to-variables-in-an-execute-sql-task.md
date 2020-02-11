---
title: Сопоставьте параметры запроса с переменными в задаче «Выполнение SQL» | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8863de6fc0418dbf502492ac20f7c5c846696aea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057798"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a>Сопоставление параметров запроса с переменными в задаче «Выполнение SQL»

  Данный раздел описывает использование параметризованной инструкции SQL в задаче «Выполнение SQL» и создание сопоставлений между переменными и параметрами в инструкции SQL.  
  
 Дополнительные сведения о задаче "Выполнение SQL", маркерах параметров и именах параметров, используемых с различными типами соединений, см. в разделах [Задача "Выполнение SQL"](control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>Сопоставление параметра запроса с переменной  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте необходимый пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** .  
  
4.  Если пакет не включает задачу «Выполнение SQL», добавьте его к потоку управления пакета. Дополнительные сведения см. [в разделе Добавление или удаление задачи или контейнера в потоке управления](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) .  
  .  
  
5.  Дважды щелкните задачу «Выполнение SQL».  
  
6.  Введите параметризированную команду SQL одним из следующих способов.  
  
    -   Используйте прямой ввод и введите команду SQL в свойство SQLStatement.  
  
    -   Используйте прямой ввод, нажмите кнопку **Создать запрос**и создайте команду SQL, используя графические средства, предоставляемые построителем запросов.  
  
    -   Используйте подключение файла и укажите ссылку на файл, содержащий команду SQL.  
  
    -   Используйте переменную и укажите ссылку на переменную, содержащую команду SQL.  
  
     Маркеры параметров, которые используются в параметризованных инструкциях SQL, зависят от типа соединения, используемого задачей «Выполнение SQL».  
  
    |Тип подключения|Маркер параметра|  
    |---------------------|----------------------|  
    |ADO|?|  
    |ADO.NET и SQLMOBILE|@\<имя параметра>|  
    |ODBC|?|  
    |EXCEL и OLE DB|?|  
  
     В следующей таблице приведен список примеров команды SELECT для разных типов диспетчеров соединений. Параметры предоставляют значения фильтра в предложениях WHERE. В примерах инструкции SELECT возвращают из таблицы **Product** базы данных [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] продукты, для которых значение **ProductID** больше и меньше значений, указанных двумя параметрами.  
  
    |Тип подключения|Синтаксис SELECT|  
    |---------------------|-------------------|  
    |EXCEL, ODBC и OLEDB|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |ADO|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     Примеры использования параметров с хранимыми процедурами см. в разделе [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
7.  Щелкните **Сопоставление параметров**.  
  
8.  Чтобы добавить сопоставление параметров, нажмите кнопку **Добавить**.  
  
9. Введите имя в поле **Имя параметра** .  
  
     Имена параметров зависят от типа соединения, используемого задачей «Выполнение SQL».  
  
    |Тип подключения|Имя параметра|  
    |---------------------|--------------------|  
    |ADO|Param1, Param2, …|  
    |ADO.NET и SQLMOBILE|@\<имя параметра>|  
    |ODBC|1, 2, 3, ...|  
    |EXCEL и OLE DB|0, 1, 2, 3, ...|  
  
10. Выберите переменную из списка **Имя переменной** . Дополнительные сведения см. в разделе [Добавление, удаление и изменение области определяемой пользователем переменной в пакете](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).  
  
11. В списке **Направление** укажите, является ли параметр входом, выходом или возвращаемым значением.  
  
12. В списке **Тип данных** укажите тип данных параметра.  
  
    > [!IMPORTANT]  
    >  Тип данных параметра должен быть совместим с типом данных переменной.  
  
13. Повторите шаги с 8 по 11 для каждого параметра инструкции SQL.  
  
    > [!IMPORTANT]  
    >  Порядок сопоставления параметров должен соответствовать порядку, в котором параметры появляются в инструкции SQL.  
  
14. Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Задача «Выполнение SQL»](control-flow/execute-sql-task.md)   
 [Параметры и коды возврата в задаче «Выполнение SQL»](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)   
 [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md)  
  
  
