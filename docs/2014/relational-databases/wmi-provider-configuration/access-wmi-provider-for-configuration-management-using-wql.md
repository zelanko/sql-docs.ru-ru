---
title: Доступ к поставщику WMI для управления конфигурацией с использованием WQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0b19bf27cdc94e70908f81523a092ba022c41601
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157684"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>производить доступ к поставщику WMI для управления конфигурацией с использованием WQL
  В данном разделе рассматривается способ выполнения инструкций языка WQL [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows применительно к поставщику WMI для управления компьютером.  
  
 В этом примере используется редактор языка WQL, WBEMtest.exe, для запуска запросов языка WQL по отношению к поставщику WMI в целях перечисления служб, сетевых протоколов и псевдонимов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="querying-services-using-wbemtest"></a>Запрос служб с помощью WBEMtest  
  
1.  Из **запустить** меню, щелкните **запуска**, а затем введите `WBEMtest`.  
  
2.  Откроется диалоговое окно приложения WBEMtest.exe. Нажмите кнопку **Соединить**.  
  
3.  В первом текстовом поле введите пространство имен поставщика WMI для управления компьютером: root\Microsoft\SqlServer\ComputerManagement11. Нажмите кнопку **Соединить**.  
  
4.  Нажмите кнопку **запроса**. Введите запрос, возвращающий текущей службы, запущенные на локальном компьютере: **ВЫБЕРИТЕ \* из SqlService.** Нажмите кнопку **Применить**.  
  
5.  Уточните запрос, добавив `WHERE ServiceName = "MSSQLSERVER"`.  
  
  
