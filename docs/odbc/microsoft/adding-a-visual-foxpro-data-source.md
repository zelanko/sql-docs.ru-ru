---
title: Добавление источника данных Visual FoxPro | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fd0c0f929ca00b7cf731dc92f07f69b6503f884
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307145"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Добавление источника данных Visual FoxPro
Для доступа к данным Visual FoxPro из приложения необходим источник данных. Источник данных можно создать следующим образом:  
  
-   В приложении, таком как Microsoft® Word, Microsoft Excel или Microsoft Access, использующие драйверы ODBC.  
  
-   За пределами приложения, используя панель управления Microsoft Windows® 95, Microsoft Windows 98 или Microsoft Windows NT®/Виндовс 2000.  
  
 После того как источник данных существует в системе, можно повторно использовать тот же источник данных каждый раз, когда требуется доступ к данным Visual FoxPro. При наличии нескольких различных баз данных или таблиц, к которым необходимо получить доступ, можно создать отдельный источник данных для каждой базы данных или каталога.  
  
 Следующая процедура создает источник данных с помощью панели управления. Дополнительные сведения о создании источника данных из приложения см. в разделе [доступ к данным Visual FoxPro из Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Добавление источника данных Visual FoxPro  
  
1.  На компьютерах под управлением Windows 2000 откройте панель управления Windows и дважды щелкните Администрирование.  
  
2.  Дважды щелкните элемент Источники данных (ODBC), чтобы открыть диалоговое окно «Администратор источников данных ODBC». Этот значок доступен после установки драйвера ODBC для Visual FoxPro или любого программного обеспечения драйвера ODBC.  
  
    > [!NOTE]  
    >  Если вы используете более раннюю версию Windows, откройте панель управления Windows и дважды щелкните 32-разрядный ODBC или ODBC, чтобы открыть диалоговое окно «Администратор источников данных ODBC».  
  
3.  Нажмите кнопку «Добавить».  
  
4.  В диалоговом окне Создание нового источника данных выберите драйвер Microsoft Visual FoxPro и нажмите кнопку Готово.  
  
5.  В [диалоговом окне Установка ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)введите имя и описание источника данных, выберите тип базы данных, базу данных или каталог, а затем нажмите кнопку ОК.  
  
     Новое имя источника данных отображается в списке источники данных пользователя на вкладке пользовательское имя пользователя диалогового окна Администратор источников данных ODBC.  
  
6.  Нажмите кнопку ОК, чтобы сохранить новый источник данных и закрыть диалоговое окно Администратор источников данных ODBC.
