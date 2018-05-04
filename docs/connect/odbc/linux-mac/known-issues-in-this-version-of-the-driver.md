---
title: Известные проблемы в этой версии драйвера для SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- known issues
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9c1ca89a8dbf3e5f71ff680e7437098f1eabb1c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="known-issues-in-this-version-of-the-driver"></a>Известные проблемы в данной версии драйвера

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Эта статья содержит список известных проблем с Microsoft ODBC Driver 13, 13.1 и 17 для SQL Server в Linux и macOS.

Дополнительные проблемы будут публиковаться в [блоге группы разработчиков драйвера Microsoft ODBC](http://blogs.msdn.com/b/sqlnativeclient/).  

- Windows, Linux и macOS преобразовать символы из области личных (PUA) или кодировки символов (EUDC) по-разному. Преобразования, выполняемые на сервере в [!INCLUDE[tsql](../../../includes/tsql_md.md)] использовать библиотеку преобразования Windows. Преобразования в драйвере использовать библиотеки Windows, Linux или macOS преобразования. Каждая библиотека может давать разные результаты при выполнении этих преобразований. Дополнительные сведения см. в статье [Символы, определяемые конечными пользователями, и символы области личных символов](http://msdn.microsoft.com/library/dd317802.aspx).

- Если клиент кодировку UTF-8, диспетчер драйверов не преобразует всегда правильно из UTF-8 в UTF-16. В настоящее время повреждение данных происходит, когда один или несколько символов в строке не являются допустимыми символами UTF-8. Символы ASCII сопоставляются правильно. Диспетчер драйверов пытается такое преобразование при вызове SQLCHAR-версий ODBC API (например, SQLDriverConnectA). Диспетчер драйверов не пытается выполнить такое преобразование при вызове SQLWCHAR-версий ODBC API (например, SQLDriverConnectW).  

- *ColumnSize* параметр **SQLBindParameter** ссылается на число символов в тип SQL, пока *BufferLength* число байтов в приложения буфер. Тем не менее если тип данных SQL `varchar(n)` или `char(n)`, приложение связывает параметр как SQL_C_CHAR или SQL_C_VARCHAR и кодировку клиента UTF-8, может получить ошибку «строковые данные, усечение справа» от драйвера, даже когда значение *ColumnSize* согласовано с размером типа данных на сервере. Эта ошибка возникает, поскольку преобразование кодировок может изменить длину данных. Например, правого апострофа символов (U + 2019) кодируется в CP-1252 как 0x92 один байт, но в кодировке UTF-8, как последовательность 0xe2 3 байта 0x80 0x99.

Например, если в качестве кодировки — UTF-8 и указать 1 для *BufferLength* и *ColumnSize* в **SQLBindParameter** для параметра out, а затем повторите попытку получить предыдущий знак, хранятся в `char(1)` столбца на сервере (CP-1252), драйвер пытается преобразовать его в кодировку UTF-8 3 байта, но не может поместиться результат в буфер 1 байт. В обратном направлении, он сравнивает *ColumnSize* с *BufferLength* в **SQLBindParameter** перед выполнением преобразования между различными кодовыми страницами на Клиент и сервер. Поскольку *ColumnSize* для 1 меньше, чем *BufferLength* , например, для 3, драйвер выдает ошибку. Чтобы избежать этой ошибки, убедитесь, что длина данных после преобразования, которые попадают в указанный буфер или столбец. Обратите внимание, что *ColumnSize* не может быть больше 8000 для `varchar(n)` типа.

## <a name="see-also"></a>См. также  
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)  

