---
title: Использовать драйвер ODBC для VFP FoxPro с приложением Visual Basic | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b77fdee70ff73772710c9758eeb2bf2594f365d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697885"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Использование драйвера ODBC для VFP FoxPro с приложением Visual Basic
Your Microsoft® Visual Basic® приложение может взаимодействовать с данных Visual FoxPro, создав элемент управления данных, который подключается к источнику данных Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Для подключения к данным Visual FoxPro, используя элемент управления данными в Visual Basic  
  
1.  Создайте источник данных с именем «test», который подключается с образцом базы данных TasTrade, включенные в Visual FoxPro. Visual FoxPro установки по умолчанию помещает TasTrade образца базы данных в расположении:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  В Visual Basic создать новую форму и поместите текстовое поле и элемент управления данные на нем.  
  
3.  Измените свойства элемента управления данными Connect следующим образом:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Измените свойство тип набора записей на следующее:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Измените свойство источник записей на следующее:  
  
    ```  
    customer  
    ```  
  
6.  Измените свойство источника данных для текстового поля на имя по умолчанию для элемента управления данными следующее:  
  
    ```  
    data1  
    ```  
  
7.  Измените свойство DataField текстового поля следующим образом:  
  
    ```  
    customer_id  
    ```  
  
8.  Форма запуска и пропуск по полям идентификатора клиента из образца базы данных Visual FoxPro TasTrade с помощью элемента управления данных.
