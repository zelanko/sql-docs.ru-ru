---
title: Использование драйвера ODBC для VFP FoxPro с приложением Visual Basic | Документация Майкрософт
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
ms.openlocfilehash: 017e8e7897b2b792d7a864dc336537d76dcad8b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087977"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Использование драйвера ODBC для VFP FoxPro с приложением Visual Basic
Приложение Microsoft® Visual Basic® может взаимодействовать с данными Visual FoxPro путем создания элемента управления данными, который подключается к источнику данных Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Подключение к данным Visual FoxPro с помощью элемента управления данными в Visual Basic  
  
1.  Создайте источник данных с именем Test, который подключается к образцу базы данных Тастраде, входящему в Visual FoxPro. Установка Visual FoxPro по умолчанию помещает образец базы данных Тастраде в расположение:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  В Visual Basic создайте новую форму и поместите на нее текстовое поле и элемент управления данными.  
  
3.  Измените свойство Connect элемента управления данными следующим образом:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Измените свойство Рекордсеттипе на следующее:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Измените свойство RecordSource на следующее:  
  
    ```  
    customer  
    ```  
  
6.  Измените свойство DataSource для текстового поля на имя по умолчанию для элемента управления данными следующим образом:  
  
    ```  
    data1  
    ```  
  
7.  Измените свойство поля в текстовом поле на следующее:  
  
    ```  
    customer_id  
    ```  
  
8.  Запустите форму и используйте элемент управления данными для пропуска полей идентификатор клиента из образца базы данных Visual FoxPro Тастраде.
