---
title: Доступ к поставщику WMI для управления конфигурацией с использованием WQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f35c895597bf19a7cc4ad20614d2d2f29521504e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313364"
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
  
  
