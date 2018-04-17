---
title: Запрашивая разрешения пользователя для сведений о соединении | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connecting to data source [ODBC], SqlConnect
- connecting to driver [ODBC], prompting user for information
- connecting to driver [ODBC], SQLConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLConnect function [ODBC], prompting user for connection information
- connecting to data source [ODBC], prompting user for information
- prompting user for connection information [ODBC]
- SQLDriverConnect function [ODBC], prompting user for connection information
ms.assetid: da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 796713fb12fe2eb70a0e7630ec558a63d7cfec4d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="prompting-the-user-for-connection-information"></a>Запрашивая разрешения пользователя для сведений о подключении
Если приложение использует **SQLConnect** и его необходимо запрашивать у пользователя сведения о соединении, например имя пользователя и пароль, он должен сделать это сам. Это позволяет приложению контролировать его «вид», он может вынудить приложение содержит код для конкретного драйвера. Это происходит, когда приложение должно запрашивать у пользователя сведения о соединении с драйвером. Это представляет невозможно ситуации для универсальных приложений, которые предназначены для работы с всех драйверов, включая драйверы, которые не существуют, если приложение создано.  
  
 **SQLDriverConnect** может запрашивать у пользователя сведения о соединении. Например, пользовательская программа, приведенные выше может передать следующую строку соединения для **SQLDriverConnect**:  
  
```  
DSN=XYZ Corp;  
```  
  
 Драйвер может затем отобразить диалоговое окно с запросом идентификаторы пользователей и пароли, как на следующем рисунке.  
  
 ![Диалоговое окно с запросом идентификаторов и паролей пользователей](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Что драйвер может запрашивать сведения о соединении особенно полезен для приложений универсальный и по вертикали. Эти приложения не должны содержать сведения, относящиеся к драйверу, а наличие драйвера запрашивать сведения, которые необходимы сохраняет эту информацию из приложения. Это показано в предыдущих двух примерах. Если приложение драйвера передается только имя источника данных, приложение не содержит все сведения, относящиеся к драйверу и таким образом не привязаны для драйвера. Когда приложения пройдет полную строку подключения к драйверу, он был привязан драйвер, который может интерпретировать эту строку.  
  
 Универсальное приложение может предпринять дальнейшие этого действия и даже указать источник данных. Когда **SQLDriverConnect** Получает пустую строку соединения, диспетчер драйверов отображает следующее диалоговое окно.  
  
 ![Диалоговое окно выбора источника данных](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 При выборе источника данных, диспетчер драйверов создает строку подключения, указав этот источник данных и передает его в драйвере. Драйвер может затем запросить пользователя для любых дополнительных сведений, которые необходимы.  
  
 Условия, при которых драйвер запрашивает пользователя управляются *DriverCompletion* флаг; имеются параметры всегда выводить запрос, запрос при необходимости или никогда не запрашивать подтверждение. Полное описание этого флага см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.
