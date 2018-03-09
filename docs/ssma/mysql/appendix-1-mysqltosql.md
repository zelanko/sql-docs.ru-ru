---
title: "Приложение - 1 (MySQLToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2d22766d-ff09-420d-ae7c-13b443e28bd0
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: feaa4b29266246702290065e851d33df7b09e3e7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="appendix---1-mysqltosql"></a>Приложение - 1 (MySQLToSQL)
Быстрый просмотр консоли SSMA параметры командной строки:  
  
|SL. Нет.|Параметр|Обязательно?|Аргумент ключа|Допустимые значения|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s или сценарий|Да|scriptfile|Допустимое имя XML-файла.<br /><br />Файл определения скрипта консоли.|  
|2|-v или переменная|нет|variablevaluefile|Допустимое имя XML-файла.<br /><br />При использовании переменных в файле скрипта этот файл нельзя.|  
|3|-c или serverconnection|нет|serverconnectionfile|Допустимое имя XML-файла.<br /><br />Этот файл содержит сведения о соединении сервера.|  
|4|-x-xmloutput|нет|xmloutputfile|Этот параметр указывает, вывод на консоль в формате XML. Если этот параметр не указан, по умолчанию выводится в ТЕКСТОВОМ формате.<br /><br />Если xmloutputfile не указан, выходные данные XML направляются в STDOUT.<br /><br />Xmloutputfile — это имя файла, в который записывается вывод на консоль в формате XML.|  
|5|-l или журнала|нет|logfile|Недопустимое имя файла.|  
|6|-e-projectenvironment|нет|projectenvironmentfolder|Допустимое имя папки с файлами среды проекта SSMA.|  
|7|-p/securepassword|нет|--Добавление {< server_id > [,... n] &#124; все} – c &#124; serverconnection < файл сервера соединения > [-v &#124; переменная < переменной значение Файл->] [-o и перезаписать]<br /><br />или диспетчер конфигурации служб<br /><br />--Добавление {< server_id > [,... n] &#124; все} – s &#124; сценарий < файл сценария > [-v &#124; variable < файл переменной значение >] [-o и перезаписать]<br /><br />-r или удалить {< server_id > [,... n] &#124; все}<br /><br />-l или списка<br /><br />– e и экспорта {< идентификатор сервера-> [,... n] &#124; все} < зашифрованного пароля - файла ><br /><br />– i / import {< идентификатор сервера-> [,... n] &#124; все} < шифрование пароля файл->|Если указан, этот параметр не должны быть объединены с любыми другими параметрами.<br /><br />Идентификатор сервера: Уникальный идентификатор, указанный для сервера {строка}<br /><br />файл для подключения сервера: сервер файл определения (serverconnectionfile или файл сценария).<br /><br />файл переменная значение: это файл определения переменных, используемых в файл для подключения сервера.<br /><br />шифрование пароля файла: файл пароли сервера, зашифрованные с помощью пользовательской парольную фразу.|  
|8|-?|нет|Неприменимо|Неприменимо|  
  
## <a name="see-also"></a>См. также:  
[Выполнение консоли SSMA (MySQL)](http://msdn.microsoft.com/en-us/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
