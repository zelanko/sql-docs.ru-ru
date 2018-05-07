---
title: Использовать драйвер ODBC для VFP FoxPro вместе с приложением Visual Basic | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 96107d42ae4923cd1b9f7ad1c16bd492d0203c99
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>С помощью драйвера ODBC для VFP FoxPro вместе с приложением Visual Basic
Ваш Microsoft® Visual Basic® приложению взаимодействовать с данными Visual FoxPro путем создания элемента управления данными, подключается к источнику данных Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Для подключения к данным Visual FoxPro, с помощью элемента управления данными в Visual Basic  
  
1.  Создайте источник данных с именем «test», подключающийся к образцу базы данных TasTrade, включенных в Visual FoxPro. Установка Visual FoxPro по умолчанию помещает TasTrade образца базы данных в расположении:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  В Visual Basic создайте новую форму и поместите текстовое поле и управления данных на нем.  
  
3.  Измените свойства элемента управления данными Connect следующим образом.  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Измените тип набора записей свойства следующим образом:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Измените свойство источник записей следующим образом:  
  
    ```  
    customer  
    ```  
  
6.  Измените свойства DataSource для текстового поля имя по умолчанию для элемента управления данными следующее:  
  
    ```  
    data1  
    ```  
  
7.  Измените свойство DataField текстовом поле следующим образом:  
  
    ```  
    customer_id  
    ```  
  
8.  Запустить форму и пропустить полей идентификатор клиента из образца базы данных Visual FoxPro TasTrade с помощью элемента управления данными.
