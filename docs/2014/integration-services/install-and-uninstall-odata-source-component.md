---
title: Установка и удаление компонента источника OData | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 039e8dd4f77c0593dcdceb69fbcd53138bc50b91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281330"
---
# <a name="install-and-uninstall-odata-source-component"></a>Установка и удаление компонента источника OData
  В этом разделе приведены инструкции по установке или удалению компонента источника OData на компьютере.  
  
## <a name="installation"></a>Установка  
 Для компонента источника OData на компьютере должны быть установлены следующие компоненты.  
  
-   SQL Server Data Tools (для проектирования пакетов)  
  
-   Службы SQL Server Integration Services (для запуска пакетов вне Visual Studio)  
  
 Чтобы установить компонент источника OData, загрузите [пакет дополнительных компонентов SQL Server 2014](http://go.microsoft.com/fwlink/p/?LinkId=391999) и запустите один из следующих MSI-файлов.  
  
-   ODataSourceForSQLServer2014-amd64.msi для 64-разрядных платформ  
  
-   ODataSourceForSQLServer2014-x86.msi для 32-разрядных платформ  
  
> [!IMPORTANT]  
>  64-разрядный установщик устанавливает 32-разрядную и 64-разрядную версии компонента источника OData. Если используется 32-разрядная ОС, необходимо запускать 32-разрядный установщик.  
  
## <a name="uninstallation"></a>Удаление  
 Компонент источника OData можно удалить в меню **Программы и компоненты** . Найдите элемент **Компонент источника OData Microsoft SQL Server SSIS (x64)** и нажмите кнопку **Удалить**.  
  
  
