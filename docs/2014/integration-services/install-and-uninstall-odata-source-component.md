---
title: Установка и удаление компонента источника OData | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ae48af3dec0be31d329548cbc0d7cd76007dacaf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095722"
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
  
  