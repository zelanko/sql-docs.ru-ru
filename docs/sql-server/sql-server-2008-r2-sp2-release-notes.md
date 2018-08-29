---
title: Заметки о выпуске SQL Server 2008 R2 с пакетом обновления 2 (SP2) | Документация Майкрософт
ms.prod: sql
ms.technology: install
ms.custom: ''
ms.date: 01/31/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server 2008 R2 SP2
- Release Notes, SQL Server 2008 R2 SP2
ms.assetid: e2bd3de7-674c-4ea7-8d53-bb40bba86fae
author: craigg-msft
ms.author: craigg
manager: jhubbard
monikerRange: = sql-server-2014 || = sqlallproducts-allversions
ms.openlocfilehash: d57f8ffc3d6fb9d1bd85bfa96f4ba431dd7fb114
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "42774608"
---
# <a name="sql-server-2008-r2-sp2-release-notes"></a>Заметки о выпуске пакета обновления 2 (SP2) для SQL Server 2008 R2
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
В этих заметках о выпуске содержится описание известных проблем, которое необходимо прочитать перед установкой или диагностикой Microsoft SQL Server 2008 R2 с пакетом обновления 2 (SP2). Эти заметки о выпуске относятся ко всем выпускам SQL Server 2008 R2 с пакетом обновления 2 (SP2) и доступны только в сети. Этот документ периодически обновляется.  
  
## <a name="10-whats-new-in-service-pack-2"></a>1.0. Новые возможности пакета обновления 2 (SP2)  
Добавлено динамическое административное представление **sys.dm_db_stats_properties**. С помощью этих динамических административных представлений можно определять статистические свойства указанной таблицы или индексированного представления из текущей базы данных. Например, это динамическое административное представление возвращает количество строк, которые были отобраны, и количество шагов в гистограмме.  
  
## <a name="20-before-you-install"></a>2.0 Перед началом установки  
Сведения об установке обновлений [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] см. в [Документации по службам SQL Server 2008 R2](http://msdn.microsoft.com/library/dd638062(SQL.105).aspx).  
  
Для получения общих сведений о начале работы и установке SQL Server 2008 R2 см. файл сведений для SQL Server 2008 R2. Файл сведений имеется на установочном носителе. Дополнительные сведения также можно найти в [электронной документации по SQL Server](sql-server-technical-documentation.md) и на [форумах по SQL Server](http://social.msdn.microsoft.com/Forums/category/sqlserver/).  
  
### <a name="21-choose-the-correct-file-to-download-and-install"></a>2.1 Выбор правильного файла для скачивания и установки  
Используйте следующую таблицу, чтобы определить, какой файл необходимо загрузить и установить. Перед установкой пакета обновления убедитесь, что соблюдены все требования к системе. Требования к системе приведены на страницах загрузки, ссылки на которые указаны в таблице.  
  
|Если текущей установленной версией является...|И необходимо выполнить следующее...|Загрузите и установите...|  
|-------------------------------------------|----------------------|---------------------------|  
|32-разрядная версия любого выпуска SQL Server 2008 R2 или SQL Server 2008 R2 с пакетом обновления 1 (SP1)|Обновление до 32-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x86-ENU [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|32-разрядная версия SQL Server 2008 R2 RTM Express или SQL Server 2008 R2 Express с пакетом обновления 1 (SP1)|Обновление до 32-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x86-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|32-разрядная версия только клиента и средств управления для SQL Server 2008 R2 или SQL Server 2008 R2 с пакетом обновления 1 (SP1) (включая SQL Server 2008 R2 Management Studio)|Обновление клиента и средств управления до 32-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x86-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|32-разрядная версия SQL Server 2008 R2 Management Studio Express или SQL Server 2008 R2 Management Studio Express с пакетом обновления 1 (SP1)|Обновление до 32-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2) Management Studio Express|SQLManagementStudio_x86_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251791)|  
|32-разрядная версия любого выпуска SQL Server 2008 R2 или SQL Server 2008 R2 с пакетом обновления 1 (SP1) **и** 32-разрядная версия клиента и средств управляемости (включая SQL Server 2008 R2 RTM Management Studio)|Обновление всех продуктов до 32-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x86-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|32-разрядная версия одного или более средств из [пакета дополнительных компонентов Microsoft SQL Server 2008 R2 RTM](http://www.microsoft.com/download/en/details.aspx?id=16978)|Обновление средств до 32-разрядной версии пакета дополнительных компонентов Microsoft SQL Server 2008 R2 с пакетом обновления 2 (SP2)|Один или несколько файлов из [пакета дополнительных компонентов Microsoft SQL Server 2008 R2 с пакетом обновления 2 (SP2)](http://go.microsoft.com/fwlink/?LinkId=251792)|  
|Отсутствует 32-разрядная установка SQL Server 2008 R2|Установка Server 2008 R2, включая пакет обновления 2 (SP2)|Перейдите по ссылке [SQL Server 2008 R2 Express Edition с пакетом обновления 2 (SP2)](http://go.microsoft.com/fwlink/?LinkId=251791) и следуйте инструкциям.|  
|Отсутствует 32-разрядная установка SQL Server 2008 R2 Management Studio|Установка среды SQL Server 2008 R2 Management Studio, включая пакет обновления 2 (SP2)|SQLManagementStudio_x86_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251791) для установки бесплатного выпуска среды SQL Server 2008 R2 с пакетом обновления 2 (SP2) Management Studio Express Edition|  
|64-разрядная версия любого выпуска SQL Server 2008 R2 или SQL Server 2008 R2 с пакетом обновления 1 (SP1)|Обновление до 64-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x64-ENU или SQLServer2008R2SP2-KB2630455-IA64-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|64-разрядная версия SQL Server 2008 R2 RTM Express или SQL Server 2008 R2 Express с пакетом обновления 1 (SP1)|Обновление до 64-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x64-ENU.exe или SQLServer2008R2SP2-KB2630455-IA64-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|64-разрядная версия только клиента и средств управляемости для SQL Server 2008 R2 или SQL Server 2008 R2 с пакетом обновления 1 (SP1) (включая SQL Server 2008 R2 Management Studio)|Обновление клиента и средств управляемости до 64-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x64-ENU.exe или SQLServer2008R2SP2-KB2630455-IA64-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|64-разрядная версия SQL Server 2008 R2 Management Studio Express или SQL Server 2008 R2 Management Studio Express с пакетом обновления 1 (SP1)|Обновление до 64-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2) Management Studio Express|SQLManagementStudio_x64_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251791)|  
|64-разрядная версия любого выпуска SQL Server 2008 R2 или SQL Server 2008 R2 с пакетом обновления 1 (SP1) **и** 64-разрядная версия клиента и средств управляемости (включая SQL Server 2008 R2 RTM Management Studio)|Обновление всех продуктов до 64-разрядной версии SQL Server 2008 R2 с пакетом обновления 2 (SP2)|SQLServer2008R2SP2-KB2630458-x64-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251790)|  
|64-разрядная версия одного или более средств из [пакета дополнительных компонентов Microsoft SQL Server 2008 R2 RTM](http://www.microsoft.com/download/en/details.aspx?id=16978)|Обновление средств до 64-разрядной версии пакета дополнительных компонентов Microsoft SQL Server 2008 R2 с пакетом обновления 2 (SP2)|Один или несколько файлов из [пакета дополнительных компонентов Microsoft SQL Server 2008 R2 с пакетом обновления 2 (SP2)](http://go.microsoft.com/fwlink/?LinkId=251792)|  
|Отсутствует 64-разрядная установка SQL Server 2008 R2|Установка Server 2008 R2, включая пакет обновления 2 (SP2)|Перейдите по ссылке [SQL Server 2008 R2 Express Edition с пакетом обновления 2 (SP2)](http://go.microsoft.com/fwlink/?LinkId=251791) и следуйте инструкциям.|  
|Отсутствует 64-разрядная установка SQL Server 2008 R2 Management Studio|Установка среды SQL Server 2008 R2 Management Studio, включая пакет обновления 2 (SP2)|SQLManagementStudio_x64_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=251791) для установки бесплатного выпуска среды SQL Server 2008 R2 с пакетом обновления 2 (SP2) Management Studio Express Edition|  
  
### <a name="22-setup-might-fail-if-sqagtresdll-is-locked-by-another-process"></a>2.2. Неудачное завершение программы установки, если файл SQAGTRES.dll заблокирован другим процессом  
**Проблема.** Программа установки SQL Server может завершить работу с этой ошибкой: `Upgrading of cluster resource C:\Program Files\Microsoft SQL Server\MSSQL10_50.<Instance name>\MSSQL\Binn\SQAGTRES.DLL on machine <Computer name> failed with Win32Exception. Please look at inner exception for details.` . Первопричиной ошибки является то, что файл C:\Windows\system32\SQAGTRES.DLL заблокирован другим процессом и программе установки не удалось обновить его.  
  
**Решение.** Переименуйте указанный выше файл, указав временное имя, такое как C:\Windows\system32\SQAGTRES_old.DLL, а затем нажмите кнопку "Повтор" в окне сообщения об ошибке установки. Это даст возможность программе установки продолжить работу. После перезагрузки можно удалить временный файл C:\Windows\system32\SQAGTRES_old.DLL.  
  
## <a name="30-known-issues-fixed-in-this-service-pack"></a>3.0. Известные проблемы, исправленные в этом пакете обновления  
Полный список ошибок и известных проблем, исправленных в этом пакете обновления, см. в следующей [статье базы знаний](http://support.microsoft.com/kb/2630455).  
  
## <a name="see-also"></a>См. также:  
[Как определить версию и выпуск SQL Server](http://support.microsoft.com/kb/321185)  
  
