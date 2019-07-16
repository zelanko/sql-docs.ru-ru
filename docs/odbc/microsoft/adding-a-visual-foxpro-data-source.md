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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5203a7216faa008aade21c4e3e1dc54fc794461b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67901443"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Добавление источника данных Visual FoxPro
Для доступа к данным Visual FoxPro из приложения, необходимо иметь источник данных. Можно создать источник данных следующим образом:  
  
-   В приложении, например Microsoft® Word, Microsoft Excel или Microsoft Access, использующей драйверы ODBC.  
  
-   За пределами вашего приложения с помощью Microsoft Windows® 95, Microsoft Windows 98 или панель управления Microsoft Windows и Windows 2000.  
  
 После источника данных существует в вашей системе, можно повторно использовать тот же источник данных каждый раз, которое вы хотите получить доступ к данным Visual FoxPro. Если у вас есть несколько разных баз данных или таблицы, которые необходимо получить доступ, можно создать отдельный источник данных для каждой базы данных или каталога.  
  
 В следующей процедуре создается источник данных с помощью панели управления. Дополнительные сведения о том, как создать источник данных из приложения, см. в разделе [доступ к Visual FoxPro данные из Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Добавление источника данных Visual FoxPro  
  
1.  На компьютерах, работающих под управлением Windows 2000 откройте панель управления Windows, а затем дважды щелкните Администрирование.  
  
2.  Дважды щелкните источники данных (ODBC) чтобы открыть диалоговое окно администратора источника данных ODBC. Этот значок доступна после установки драйвера ODBC для Visual FoxPro или программное обеспечение драйвера ODBC.  
  
    > [!NOTE]  
    >  При использовании более ранней версии Windows, откройте панель управления Windows и дважды щелкните 32-разрядный ODBC или ODBC, чтобы открыть диалоговое окно администратора источника данных ODBC.  
  
3.  Нажмите кнопку «Добавить».  
  
4.  В диалоговом окне Создание нового источника данных выберите Microsoft Visual FoxPro драйвер и нажмите кнопку Готово.  
  
5.  В [диалоговое окно настройки ODBC для Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), введите имя источника данных и описание, выберите тип базы данных, выберите базу данных или каталог и нажмите кнопку ОК.  
  
     Имя источника данных отображается в списке источников данных пользователя на вкладке "DSN пользователя" диалогового окна "Источники данных ODBC".  
  
6.  Нажмите кнопку ОК, чтобы сохранить новый источник данных и закрыть диалоговое окно администратора источника данных ODBC.
