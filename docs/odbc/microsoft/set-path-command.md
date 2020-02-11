---
title: Команда SET PATH | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 57685731bc5eb86381816d0cbb91a4942b5bfeff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063639"
---
# <a name="set-path-command"></a>Команда SET PATH
Указывает путь для поиска файлов. Сведения, относящиеся к драйверу, см. в разделе Примечания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Аргументы  
 В [ *path*]  
 Указывает каталоги, в которых требуется выполнять поиск в Visual FoxPro. Для разделения каталогов используйте запятые или точки с запятой.  
  
## <a name="remarks"></a>Remarks  
 ЗАДАТЬ путь позволяет указать пути поиска для других программ Visual FoxPro, которые могут вызываться в хранимых процедурах. SET PATH не изменит путь к источнику данных, указанному для соединения.  
  
 Выдача пути к параметру без *пути* для восстановления пути к каталогу или папке по умолчанию.  
  
## <a name="driver-remarks"></a>Примечания к драйверам  
 Если вы выдаете параметр PATH в хранимой процедуре, он будет проигнорирован следующими функциями и командами:  
  
-   Функции каталога, такие как [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) и [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) , игнорируют новый путь и продолжают ссылаться на путь, указанный в источнике данных в [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) или [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   Такие команды, как SELECT, INSERT, UPDATE, DELETE и CREATE TABLE, пропускают новый путь и продолжают ссылаться на путь, указанный в источнике данных в **SQLPrepare** или **SQLExecDirect**.  
  
 Если вы выдаете параметр PATH в хранимой процедуре и не устанавливаете путь обратно в исходное состояние, то другие соединения с базой данных будут использовать новый путь (так как для установки пути не используется сеансы данных).  
  
 Если необходимо создать, выбрать или обновить таблицы в каталоге, отличном от указанного в источнике данных, укажите полный путь к файлу с помощью команды.  
  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно установки ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
