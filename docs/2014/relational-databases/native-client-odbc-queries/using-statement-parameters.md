---
title: Использование параметров инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a16f070623503dcb17788bc75bd5695bc1584d7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155560"
---
# <a name="using-statement-parameters"></a>Использование параметров инструкции
  Параметр — это переменная в инструкции SQL, позволяющая в приложении ODBC осуществлять следующее.  
  
-   Эффективно передавать значения для столбцов таблицы.  
  
-   Повышать степень взаимодействия с пользователем при конструировании критериев запроса.  
  
-   Управление **текст**, **ntext**, и **изображение** данных и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-определенные типы данных C.  
  
 Например **частей** таблица содержит столбцы с именем **PartID**, **описание**, и **цена**. Для добавления компонента без параметров необходимо составить инструкцию SQL, например:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Эта инструкция вполне подходит для вставки одной строки с заранее известным набором значений, но если в приложении необходимо вставить несколько строк, она становится менее приемлемой. Поэтому в ODBC разрешается заменять в приложении любое значение данных в инструкции SQL маркером параметра. Он обозначается вопросительным знаком (?). В следующем примере маркерами параметров заменены три значения данных.  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Затем происходит привязка маркеров параметров к переменным приложения. Для вставки новой строки в приложении достаточно только задать значения параметров и выполнить инструкцию. После этого драйвер получает текущие значения переменных и передает их в источник данных. Если инструкция выполняется неоднократно, то в приложении можно дополнительно оптимизировать этот процесс с помощью подготовки инструкции.  
  
 Ссылка на каждый маркер параметра осуществляется по порядковому номеру; параметры нумеруются слева направо. Первый слева параметр в инструкции SQL имеет порядковый номер 1; следующий — 2 и т. д.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Привязка параметров](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
