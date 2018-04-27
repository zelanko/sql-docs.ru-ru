---
title: Приложение - 1 (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Appendix
ms.assetid: 6dcfd6d5-772c-4876-aa94-a7f43c4b9d59
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 184ee95eaa82002813ee37492da0f6193730567e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="appendix---1-sybasetosql"></a>Приложение - 1 (SybaseToSQL)
Быстрый просмотр консоли SSMA параметры командной строки:  
  
|SL. Нет.|Параметр|Обязательно?|Аргумент ключа|Допустимые значения|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s или сценарий|Да|scriptfile|Допустимое имя XML-файла.<br /><br />Файл определения скрипта консоли.|  
|2|-v или переменная|Нет|variablevaluefile|Допустимое имя XML-файла.<br /><br />При использовании переменных в файле скрипта этот файл нельзя.|  
|3|-c или serverconnection|Нет|serverconnectionfile|Допустимое имя XML-файла.<br /><br />Этот файл содержит сведения о соединении сервера.|  
|4|-x-xmloutput|Нет|xmloutputfile|Этот параметр указывает, вывод на консоль в формате XML. Если этот параметр не указан, по умолчанию выводится в ТЕКСТОВОМ формате.<br /><br />Если xmloutputfile не указан, выходные данные XML направляются в STDOUT.<br /><br />Xmloutputfile — это имя файла, в который записывается вывод на консоль в формате XML.|  
|5|-l или журнала|Нет|logfile|Недопустимое имя файла.|  
|6|-e-projectenvironment|Нет|projectenvironmentfolder|Допустимое имя папки с файлами среды проекта SSMA.|  
|7|-p/securepassword|Нет|--Добавление {<server_id> [,...n] &#124;все} –c&#124;serverconnection <файл сервера соединения> [-v&#124;переменная <переменной значение Файл->] [-o и перезаписать]<br /><br />либо<br /><br />--Добавление {<server_id> [,...n] &#124;все} –s&#124;сценарий <файл сценария> [-v&#124;variable <файл переменной значение>] [-o и перезаписать]<br /><br />-r или удалить {< server_id > [,... n] &#124; все}<br /><br />-l или списка<br /><br />– e и экспорта {< идентификатор сервера-> [,... n] &#124; все} < зашифрованного пароля - файла ><br /><br />– i / import {< идентификатор сервера-> [,... n] &#124; все} < шифрование пароля файл->|Если указан, этот параметр не должны быть объединены с любыми другими параметрами.<br /><br />Идентификатор сервера: Уникальный идентификатор, указанный для сервера {строка}<br /><br />файл для подключения сервера: сервер файл определения (serverconnectionfile или файл сценария).<br /><br />файл переменная значение: это файл определения переменных, используемых в файл для подключения сервера.<br /><br />шифрование пароля файла: файл пароли сервера, зашифрованные с помощью пользовательской парольную фразу.|  
|8|-?|Нет|Неприменимо|Неприменимо|  
  
## <a name="see-also"></a>См. также  
[Выполнение консоли SSMA (Sybase)](http://msdn.microsoft.com/en-us/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
