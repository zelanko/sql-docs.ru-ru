---
title: Используйте Драйвер VFP FoxPro ODBC с вашим визуальным базовым приложением (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 871c392166fa2f5726e6f9e8651bf758dc144a00
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292704"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Использование драйвера ODBC для VFP FoxPro с приложением Visual Basic
Приложение Microsoft® Visual Basic® может общаться с данными Visual FoxPro, создавая элемент управления данными, который подключается к источнику данных Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Подключение к визуальным данным FoxPro с помощью управления данными в Visual Basic  
  
1.  Создайте источник данных под названием "тест", который подключается к выборочной базе данных TasTrade, включенной в Visual FoxPro. Установка Visual FoxPro по умолчанию помещает образец базы данных TasTrade в место:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  В Visual Basic создайте новую форму и разместите на нем текстовый ящик и элемент управления данными.  
  
3.  Измените свойство подключения управления данными следующим образом:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Измените свойство RecordsetType на следующее:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Измените свойство RecordSource на следующее:  
  
    ```  
    customer  
    ```  
  
6.  Измените свойство DataSource для текстового поля на имя по умолчанию для управления данными на следующее:  
  
    ```  
    data1  
    ```  
  
7.  Измените свойство DataField текстового поля на следующее:  
  
    ```  
    customer_id  
    ```  
  
8.  Запустите форму и используйте элемент управления данными, чтобы пропустить поля идентификатора клиента из базы данных Visual FoxPro TasTrade.
