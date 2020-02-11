---
title: Импорт данных Visual FoxPro в Microsoft Access | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 557b5505b9eb6a15080a7d0495df2e63aefd2d76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085546"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Импорт данных Visual FoxPro в Microsoft Access
Данные, хранящиеся в базе данных Visual FoxPro, можно импортировать в базу данных Microsoft Access с помощью параметра импорта.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Импорт данных Visual FoxPro в базу данных Microsoft Access  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  В меню Файл выберите получить внешние данные, а затем импорт.  
  
3.  В диалоговом окне Импорт выберите базы данных ODBC в списке Тип файлов.  
  
4.  В диалоговом окне Источники данных SQL выберите источник данных Visual FoxPro, который подключается к данным FoxPro, к которым необходимо выполнить запрос, и нажмите кнопку ОК.  
  
5.  В диалоговом окне Импорт объектов выберите одну или несколько таблиц, которые необходимо импортировать, и нажмите кнопку ОК. Имена импортированных таблиц Visual FoxPro отображаются на вкладке таблицы базы данных Microsoft Access.  
  
 Теперь можно использовать Microsoft Access для работы с данными в импортированных таблицах Visual FoxPro. Импортируемые данные являются моментальным снимком данных, хранящихся в Visual FoxPro; изменения, вносимые в импортированные данные, не отправляются обратно в источник данных Visual FoxPro.  
  
 Если вы хотите, чтобы изменения, вносимые в Microsoft Access, изменяли данные в источнике данных Visual FoxPro, см. статью [запросы и обновление данных Visual FoxPro из Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
