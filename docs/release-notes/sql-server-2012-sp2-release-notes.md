---
title: "Заметки о выпуске SQL Server 2012 с пакетом обновления 2 (SP2) | Документация Майкрософт"
ms.prod: sql-server-2012
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5e132652cc6464502785647f8a79dec5e25094c4
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-2012-sp2-release-notes"></a>Заметки о выпуске SQL Server 2012 с пакетом обновления 2 (SP2)
Данные Заметки о выпуске описывают вопросы, которые вам необходимо знать перед установкой или устранением проблем пакета обновлений 2 SQL Server 2012. Заметки о выпуске доступны только в сети Интернет, а не на установочном носителе. Они периодически обновляются при добавлении новых вопросов. Дополнительную информацию смотри в [исправленные ошибки в пакете обновлений 2 SQL Server 2012](http://support.microsoft.com/KB/2958429) .  
  
## <a name="choose-the-correct-file-to-download-and-install"></a>Выберите правильный файл для загрузки и установите его  
Используйте таблицу, приведенную ниже, для определения расположения и имени файла для загрузки, основанные на вашей текущей установленной версии. Страницы загрузки содержат требования к системе и основные инструкции по установке.  
  
||||  
|-|-|-|  
|**Текущая установленная версия...**|**И необходимо выполнить следующее...**|**Загрузите и установите...**|  
|32-разрядные установки:|||  
|32-разрядная версия любого выпуска SQL Server 2012|Обновление до 32-разрядной версии SQL Server 2012 SP2|**SQLServer2012SP2-KB2958429-**<arch>**-**<lang id>**.exe** со [страницы для скачивания SQL Server 2012 с пакетом обновления 2 (SP2)](http://go.microsoft.com/fwlink/?LinkID=401006)|  
|32-разрядная версия SQL Server 2012 RTM Express|Обновление до 32-разрядной версии SQL Server 2012 Express SP2|**SQLEXPR_**<arch>**_**<lang>**.msi** со [страницы для скачивания файлов SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|32-разрядная версия только клиента и средств управления для SQL Server 2012 (включая SQL Server 2012 Management Studio)|Обновление клиента и средств управления до 32-разрядной версии SQL Server 2012 SP2|**SQLEXPRWT_**<arch>**_**<lang>**.msi** со [страницы для скачивания файлов SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|32-разрядная версия SQL Server 2012 Management Studio Express|Обновление до 32-разрядной версии SQL Server 2012 SP2 Management Studio Express|**SQLManagementStudio_**<arch>**_**<lang>**.msi** со [страницы для скачивания файлов SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|32-разрядная версия любого выпуска SQL Server 2012 и 32-разрядная версия клиента и средств управления (включая SQL Server 2012 RTM Management Studio)|Обновление всех продуктов до 32-разрядной версии SQL Server 2012 SP2|**SQLEXPRADV_**<arch>**_**<lang>**.msi** со [страницы для скачивания файлов SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|32-разрядная версия одного или нескольких средств со страницы [Пакет дополнительных компонентов Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/details.aspx?id=29065) или [Пакет дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](http://go.microsoft.com/fwlink/p/?LinkID=268266)|Обновление средств до 32-разрядной версии пакета дополнительных компонентов Microsoft SQL Server 2012 SP2|Одно ли несколько средств со страницы загрузки [Пакет дополнительных компонентов Microsoft SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401008)|  
|Установки 64-разрядной версии:|||  
|64-разрядная версия любого выпуска SQL Server 2012|Обновление до 64-разрядной версии SQL Server 2012 SP2|SQLServer2012SP2-KB2958429-<arch>-<langid>.exe со [страницы для скачивания SQL Server 2012 с пакетом обновления 2 (SP2)](http://go.microsoft.com/fwlink/?LinkID=401006)|  
|64-разрядная версия SQL Server 2012 RTM Express|Обновление до 64-разрядной версии SQL Server 2012 SP2|**SQLEXPR_**<arch>**_**<lang>**.msi** со [страницы для скачивания файлов SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|64-разрядная версия только клиента и средств управляемости для SQL Server 2012 (включая SQL Server 2012 Management Studio)|Обновление клиента и средств управления до 64-разрядной версии SQL Server 2012 SP2|**SQLEXPRWT_**<arch>**_**<lang>**.msi** со [страницы для скачивания файлов SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|64-разрядная версия SQL Server 2012 Management Studio Express|Обновление до 64-разрядной версии SQL Server 2012 SP2 Management Studio Express|**SQLManagementStudio_**<arch>**_**<lang>**.msi** со [страницы для скачивания файлов SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|64-разрядная версия одного или нескольких средств со страницы [Пакет дополнительных компонентов Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/details.aspx?id=29065) или [Пакет дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](http://go.microsoft.com/fwlink/p/?LinkID=268266)|Обновите средства до 64-разрядной версии Пакета дополнительных компонентов Microsoft SQL Server 2012 SP2|Одно ли несколько средств со страницы загрузки [Пакет дополнительных компонентов Microsoft SQL Server 2012 SP2](http://go.microsoft.com/fwlink/?LinkID=401008)|  
  

