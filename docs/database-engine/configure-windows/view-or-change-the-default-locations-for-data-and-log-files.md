---
title: Просмотр или изменение расположения по умолчанию для файлов данных и журнала | Документы Майкрософт
description: Узнайте, как просматривать или изменять расположения по умолчанию для файлов данных и журнала SQL Server. Ознакомьтесь с возможностями защиты файлов с помощью списков управления доступом (ACL).
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d20175640070884a45d9a7230fb4da0f09afc0f1
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670720"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>Просмотр или изменение расположения по умолчанию для файлов данных и журнала
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
 Рекомендуемым способом защиты файлов данных и журналов является защита с помощью списков управления доступом (ACL). Задайте в качестве расположения списков ACL корневой каталог, где создаются файлы.  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>Просмотр или изменение расположений по умолчанию для файлов базы данных  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите **Свойства**.  
  
2.  На странице "Свойства" левой панели откройте вкладку **Параметры базы данных** .  
  
3.  В области **Места хранения, используемые базой данных по умолчанию**можно просмотреть текущие расположения, используемые по умолчанию для новых файлов данных и файлов журнала. Чтобы изменить местоположение по умолчанию, введите новый путь по умолчанию в поле **Данные** или **Журнал** или нажмите кнопку обзора, перейдите к нужному пути и выберите его.  
  
>**ПРИМЕЧАНИЕ.** После изменения расположений по умолчанию необходимо остановить и запустить службу SQL Server, чтобы завершить изменение.  
  
## <a name="see-also"></a>См. также раздел  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md)   
 [Создание базы данных](../../relational-databases/databases/create-a-database.md)  
  
