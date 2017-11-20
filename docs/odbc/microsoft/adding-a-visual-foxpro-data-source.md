---
title: "Добавление источника данных Visual FoxPro | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d158cf38e5755e0e443d6cb47e4053bd05d45287
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="adding-a-visual-foxpro-data-source"></a>Добавление источника данных Visual FoxPro
Доступ к данным Visual FoxPro из приложения, необходимо иметь источник данных. Источник данных можно создать следующим образом:  
  
-   В приложении, таком как Microsoft® Word, Microsoft Excel или Microsoft Access, использующей драйверов ODBC.  
  
-   За пределами приложения с помощью Microsoft Windows® 95, Microsoft Windows 98 или панель управления Microsoft Windows или Windows 2000.  
  
 После источника данных существует в системе, можно повторно использовать тот же источник данных каждый раз, необходимо получить доступ к данным Visual FoxPro. Если у вас есть несколько разных баз данных или таблицы, которые необходимо получить доступ к, можно создать отдельного источника данных для каждой базы данных или каталога.  
  
 В следующей процедуре создается источник данных с помощью панели управления. Дополнительные сведения о том, как создать источник данных из приложения, см. в разделе [Visual FoxPro данным с Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Добавление источника данных Visual FoxPro  
  
1.  На компьютерах, работающих под управлением Windows 2000 откройте панель управления Windows и дважды щелкните значок Администрирование.  
  
2.  Дважды щелкните источники данных (ODBC), чтобы открыть диалоговое окно администратора источника данных ODBC. Этот значок доступна после установки драйвера ODBC для Visual FoxPro или любое программное обеспечение драйвера ODBC.  
  
    > [!NOTE]  
    >  При использовании более ранней версии Windows, откройте панель управления Windows и дважды щелкните 32-разрядных ODBC или ODBC, чтобы открыть диалоговое окно администратора источника данных ODBC.  
  
3.  Нажмите кнопку «Добавить».  
  
4.  В диалоговом окне Создание нового источника данных выберите Microsoft Visual FoxPro драйвер и нажмите кнопку Готово.  
  
5.  В [диалоговое окно установки Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), введите имя источника данных и описание, выберите тип базы данных, выберите базу данных или каталог и нажмите кнопку ОК.  
  
     Имя источника данных отображается в списке источников данных пользователя на вкладке DSN пользователя диалоговое окно администратора источника данных ODBC.  
  
6.  Нажмите кнопку ОК, чтобы сохранить новый источник данных и закрыть диалоговое окно администратора источника данных ODBC.

