---
description: Установка расширений в SQL Server Management Studio (SSMS)
title: Установка расширений в SQL Server Management Studio (SSMS)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
keywords:
- extensions
- vsix
- установка расширения
- установка vsix
author: dzsquared
ms.author: drskwier
ms.reviewer: maghan
ms.custom: seo-lt-2019
ms.date: 07/29/2020
ms.openlocfilehash: bf4c9ee5287a2e0fdecf8455334561ce130499bc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492058"
---
# <a name="install-extensions-in-sql-server-management-studio-ssms"></a>Установка расширений в SQL Server Management Studio (SSMS)

[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

Расширения SQL Server Management Studio (SSMS) созданы на C# с помощью рабочей нагрузки "Разработка расширения Visual Studio" в Visual Studio. SSMS 18.x основана на оболочке Visual Studio 2017 и зависит от ограничений этой среды.

Установку расширения в SSMS 18.x можно выполнить путем развертывания VSIX с помощью Visual Studio или независимого управляемого установщика пакетов.  Развертывание в Visual Studio описано ниже.

> [!NOTE]
> Расширения SQL Server Management Studio невозможно установить через VSIXInstaller в SSMS 18.x.
  
## <a name="visual-studio-deployment-of-an-extension-for-ssms-18x"></a>Развертывание расширения для SSMS 18.x в Visual Studio

Установка расширения вручную выполняется путем копирования соответствующих файлов расширения (VSIX) в папку расширений SSMS по умолчанию.  SSMS автоматически проверяет эту папку при запуске на наличие расширений.  Развертывание VSIX Visual Studio может выполнять во время сборки проекта. 

  
1.  Найдите расположение установки SSMS и папки расширений по умолчанию.  В параметрах установки SSMS расположение папки по умолчанию — ```C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\Extensions\```.  


2. Запустите Visual Studio от имени администратора.

3.  Процесс копирования файлов в Visual Studio может выполняться во время сборки, если установить флажок "Копировать содержимое VSIX в следующее расположение" на вкладке окна свойств проекта VSIX. В текстовом поле под флажком введите расположение найденной выше папки и папки этого расширения.  Пример: ```C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\Extensions\SampleExtension```
  
![Окно свойств проекта для параметров VSIX с тремя флажками и текстовым полем](./media/install-extensions/vsix_ssms.png)

4. Выполните сборку проекта расширения. В результате успешной сборки файлы расширения будут перенесены в папку расширения SSMS.

5.  Запустите SSMS и проверьте функциональность расширения.
  
