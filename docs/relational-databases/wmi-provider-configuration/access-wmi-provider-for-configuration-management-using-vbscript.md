---
title: Доступ к поставщику WMI с помощью VBScript
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a5415e9d425087f42e3058328f061660ffbe8c1e
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73658953"
---
# <a name="access-wmi-provider-for-configuration-management-using-vbscript"></a>Доступ к поставщику WMI для управления конфигурацией с использованием VBScript
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается создание программы VBScript, которая содержит версию установленных экземпляров [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], работающих на компьютере.  
  
 В этом примере кода перечисляются экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенные на компьютере, и их версии.  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a>Список имен и версий установленных экземпляров SQL Server  
  
1.  Откройте новый документ в текстовом редакторе, например в [!INCLUDE[msCoName](../../includes/msconame-md.md)] блокноте. Скопируйте код, который следует за данной процедурой, и сохраните файл с расширением VBS. Этот пример называется test.vbs.  
  
2.  Подключитесь к экземпляру поставщика WMI при помощи функции `GetObject` языка VBScript. В данном примере выполняется подключение к удаленному компьютеру с именем mpc, но не указывается имя компьютера для подключения к локальному компьютеру: winmgmts:root\Microsoft\SqlServer\ComputerManagement. Дополнительные сведения о функции `GetObject` см. в справочнике по VBScript.  
  
3.  Метод `InstancesOf` используется для перечисления списка служб. Вместо метода `ExecQuery` службы можно перечислить при помощи простого WQL-запроса и метода `InstancesOf`.  
  
4.  Воспользуйтесь методами `ExecQuery` и WQL-запросом для доступа к именам и версиям установленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Сохраните файл.  
  
6.  Запустите скрипт, введя **cscript Test. vbs** в командной строке.  

## <a name="example"></a>Пример  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
