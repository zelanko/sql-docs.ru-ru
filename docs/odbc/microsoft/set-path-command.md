---
title: Команда SET PATH Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e44093c3ea18bc995264a8974726f5af0abe3b3a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300824"
---
# <a name="set-path-command"></a>Команда SET PATH
Определяется путь поиска файлов. Для получения информации о конкретной для водителей см.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Аргументы  
 Путь к *пути*  
 Определяет каталоги, которые вы хотите, чтобы Visual FoxPro для поиска. Используйте запятые или запятые для разделения каталогов.  
  
## <a name="remarks"></a>Remarks  
 SET PATH позволяет указать пути поиска для других программ Visual FoxPro, которые можно вызвать в рамках сохраненных процедур. SET PATH не изменит траекторию источника данных, указанного для соединения.  
  
 Выпуск SET PATH TO без *Пути* для восстановления пути к каталогу или папке по умолчанию.  
  
## <a name="driver-remarks"></a>Замечания водителя  
 Если вы оформляете SET PATH в сохраненной процедуре, он будет проигнорирован следующими функциями и командами:  
  
-   Функции каталога, такие как [S'LTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) и [S'LColumns,](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) будут игнорировать новый путь и продолжать ссылаться на путь, указанный источником данных в [S'LPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) или [S'LExecDirect.](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)  
  
-   Команды, такие как SELECT, INSERT, UPDATE, DELETE и CREATE TABLE, будут игнорировать новый путь и продолжать ссылаться на путь, указанный источником данных в **S'LPrepare** или **S'LExecDirect.**  
  
 Если вы оформляете SET PATH в сохраненной процедуре и впоследствии не устанавливаете путь обратно в исходное состояние, другие соединения с базой данных будут использовать новый путь (потому что SET PATH не пригодится к сеансам данных).  
  
 Если требуется создать, выбрать или обновить таблицы в каталоге, кроме того, который указан источником данных, укажите полный путь файла с вашей командой.  
  
## <a name="see-also"></a>См. также:  
 [ODBC Визуальная FoxPro Настройка Диалог Box](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [S'LКолонки (Визуальный водитель FoxPro ODBC)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SLDriverConnect (Визуальный драйвер FoxPro ODBC)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
