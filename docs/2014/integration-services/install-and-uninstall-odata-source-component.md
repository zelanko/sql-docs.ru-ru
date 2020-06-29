---
title: Установка и удаление компонента источника OData | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c22c7c88e57c354b92bcb69429a9ab6c06ca368d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436581"
---
# <a name="install-and-uninstall-odata-source-component"></a>Установка и удаление компонента источника OData
  В этом разделе приведены инструкции по установке или удалению компонента источника OData на компьютере.  
  
## <a name="installation"></a>Установка  
 Для компонента источника OData на компьютере должны быть установлены следующие компоненты.  
  
-   SQL Server Data Tools (для проектирования пакетов)  
  
-   Службы SQL Server Integration Services (для запуска пакетов вне Visual Studio)  
  
 Чтобы установить компонент источника OData, загрузите [пакет дополнительных компонентов SQL Server 2014](https://go.microsoft.com/fwlink/p/?LinkId=391999) и запустите один из следующих MSI-файлов.  
  
-   ODataSourceForSQLServer2014-amd64.msi для 64-разрядных платформ  
  
-   ODataSourceForSQLServer2014-x86.msi для 32-разрядных платформ  
  
> [!IMPORTANT]  
>  64-разрядный установщик устанавливает 32-разрядную и 64-разрядную версии компонента источника OData. Если используется 32-разрядная ОС, необходимо запускать 32-разрядный установщик.  
  
## <a name="uninstallation"></a>Удаление  
 Компонент источника OData можно удалить в меню **Программы и компоненты** . Найдите элемент **Компонент источника OData Microsoft SQL Server SSIS (x64)** и нажмите кнопку **Удалить**.  
  
  
