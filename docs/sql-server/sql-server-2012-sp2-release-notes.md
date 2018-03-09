---
title: "Заметки о выпуске SQL Server 2012 с пакетом обновления 2 (SP2) | Документация Майкрософт"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: 
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31f86cebfc5dc23aac8d56a1a9c75d140b744063
ms.sourcegitcommit: f0c5e37c138be5fb2cbb93e9f2ded307665b54ea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2018
---
# <a name="sql-server-2012-sp2-release-notes"></a>Заметки о выпуске SQL Server 2012 с пакетом обновления 2 (SP2)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
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
  
