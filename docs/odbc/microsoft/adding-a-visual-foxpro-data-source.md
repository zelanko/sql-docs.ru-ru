---
title: Добавление визуального источника данных FoxPro (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307145"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Добавление источника данных Visual FoxPro
Чтобы получить доступ к данным Visual FoxPro из приложения, необходимо иметь источник данных. Можно создать источник данных следующим образом:  
  
-   В приложении, например Microsoft® Word, Microsoft Excel или Microsoft Access, которое использует драйверы ODBC.  
  
-   Вне приложения, используя Microsoft Windows® 95, Microsoft Windows 98, или Microsoft Windows NT®/Windows 2000 панель управления.  
  
 После того, как в вашей системе существует источник данных, вы можете повторно использовать один и тот же источник данных каждый раз, когда вы хотите получить доступ к данным Visual FoxPro. Если у вас есть несколько различных баз данных или таблиц, к которые вы хотите получить доступ, можно создать отдельный источник данных для каждой базы данных или каталога.  
  
 Следующая процедура создает источник данных с помощью панели управления. Для получения дополнительной информации о том, как создать источник данных из приложения, [см. Доступ к визуальным данным FoxPro от Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Добавление визуального источника данных FoxPro  
  
1.  На компьютерах, работающих под управлением Windows 2000, откройте панель управления Windows и дважды щелкните административные инструменты.  
  
2.  Дважды щелкните источники данных (ODBC), чтобы открыть диалоговую будку администратора источников данных ODBC. Этот значок доступен после установки Visual FoxPro ODBC Driver или любого программного обеспечения драйвера ODBC.  
  
    > [!NOTE]  
    >  Если вы работаете более раннюю версию Windows, откройте панель управления Windows и дважды нажмите 32-битный ODBC или ODBC, чтобы открыть диалоговую будку администратора источников данных ODBC.  
  
3.  Нажмите кнопку «Добавить».  
  
4.  В поле для создания нового источника данных выберите Microsoft Visual FoxPro Driver, а затем нажмите "Завершение".  
  
5.  В [диалоговом окне ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)введите имя и описание источника данных, выберите тип базы данных, выберите базу данных или каталог, а затем нажмите OK.  
  
     Новое имя источника данных отображается в списке источников пользовательских данных во вкладке Пользователь DSN в диалоговом поле odBC Data Source Administrator.  
  
6.  Нажмите OK, чтобы сохранить новый источник данных и закрыть диалоговую будку администратора данных ODBC Data Administrator.
