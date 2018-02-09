---
title: "Использование ADO с языками сценариев | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripting languages [ADO]
- ADO, scripting languages
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 804365750839fd3b9830a9573ab2cf397b529187
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="using-ado-with-scripting-languages"></a>Использование ADO с языки сценариев
В среде скриптов ADO позволяет предоставлять данные посредством скриптов на стороне сервера. В этом случае ADO базового поставщика OLE DB, он использует, и другие компоненты, необходимые для ссылки на хранилище данных установлены на сервере под управлением служб Internet Information Services (IIS). С помощью Active Server Pages (ASP), ADO — это компонент, на которые ссылается скрипт, который можно создать HTML, например. Это содержимое HTML могут передаваться через протокол HTTP для веб-браузер клиента. С помощью скриптов, веб-страницы могут отправлять действия обратно серверных скриптов, позволяя обновить, проходят через или просматривать определенные данные.  
  
 Прежде чем использовать объект ActiveX на веб-странице, важно знать, является ли объект безопасные для использования. Когда объект считается как безопасный для сценариев, это означает, что элемент управления не может выполнять любые вредоносные действия на компьютере пользователя и поэтому могут выполняться без запроса разрешения пользователя. В следующей таблице перечислены объекты ADO и указывает, является ли они безопасные для использования.  
  
|Объект|Безопасно для создания сценариев?|  
|------------|-------------------------|  
|Соединение ADO|Да|  
|Команды ADO|нет|  
|Параметр ADO|нет|  
|Набор записей ADO|Да|  
|Записей ADO|Да|  
|Поток ADO|Да|  
|Ошибка ADO|нет|  
|Каталог ADOX|нет|  
|Набор ячеек ADOX|нет|  
|DataControl служб удаленных рабочих СТОЛОВ|Да|  
|Пространство данных служб удаленных рабочих СТОЛОВ|Да|  
|DataFactory служб удаленных рабочих СТОЛОВ|нет|  
  
 В следующей таблице перечислены поставщики, включенные с Windows DAC или MDAC и указывает, является ли они безопасные для использования.  
  
|Поставщик|Безопасно для создания сценариев?|  
|--------------|-------------------------|  
|Фигурная|Да|  
|Сохранение|Да|  
|Remote|Да|  
|Поставщик OLE DB для SQL Server (SQLOLEDB)|нет|  
|Поставщик OLE DB для ODBC (MSDASQL)|нет|  
  
## <a name="odbc-data-sources"></a>Источники данных ODBC  
 Примечательным отличием между кодом ADO, сценариев и не сценариев является источник данных ODBC, если. Для приложений, отличных от сценариев можно создать пользовательское имя DSN в администраторе источников данных ODBC. Для сценариев, выполняющихся в службах IIS необходимо создать системный DSN; в противном случае скрипты не распознает созданный источник данных. Это относится к любой сценариев приложения ADO, используя поставщик Microsoft OLE DB для ODBC через Microsoft IIS.  
  
## <a name="referencing-the-ado-library"></a>Ссылающаяся на библиотеку ADO  
 Не применяется с языки сценариев.  
  
## <a name="handling-events"></a>Обработка событий  
 Не применяется с языки сценариев.  
  
 Следующие разделы содержат более подробные сведения об использовании ADO с языки сценариев:  
  
-   [Программирование объектов ADO с использованием VBScript](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [Программирование объектов ADO с использованием JScript](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>См. также  
 [Объекты данных Microsoft ActiveX (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Использование ADO с помощью Microsoft Visual Basic](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Использование объектов ADO с Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   
