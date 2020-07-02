---
title: Использование WQL для доступа к поставщику WMI
description: Используйте этот пример, чтобы узнать, как выполнять инструкции языка запросов инструментарий управления Windows (WMI) для поставщика WMI для управления компьютером в SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6e9dc2e3d0faee311945552c485187c8179f3615
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715138"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>производить доступ к поставщику WMI для управления конфигурацией с использованием WQL
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]
  В данном разделе рассматривается способ выполнения инструкций языка WQL [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows применительно к поставщику WMI для управления компьютером.  
  
 В этом примере используется редактор языка WQL, WBEMtest.exe, для запуска запросов языка WQL по отношению к поставщику WMI в целях перечисления служб, сетевых протоколов и псевдонимов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="querying-services-using-wbemtest"></a>Запрос служб с помощью WBEMtest  
  
1.  В меню **Пуск** выберите пункт **выполнить**и введите **WBEMTest**.  
  
2.  Откроется диалоговое окно приложения WBEMtest.exe. Нажмите кнопку **Соединить**.  
  
3.  В первом текстовом поле введите пространство имен поставщика WMI для управления компьютером: root\Microsoft\SqlServer\ComputerManagement11. Нажмите кнопку **Соединить**.  
  
4.  Нажмите кнопку **Запрос**. Введите запрос, который возвращает текущие службы, выполняющиеся на локальном компьютере: **выберите \* из SqlService.** Нажмите кнопку **Применить**.  
  
5.  Уточните запрос, добавив **WHERE ServiceName = "MSSQLSERVER"**.  
  
  
