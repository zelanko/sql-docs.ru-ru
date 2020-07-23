---
title: Программное управление пакетами и папками | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c45f6a5b59a65046a0e48fd930fd27d689c0a0a
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913316"
---
# <a name="managing-packages-and-folders-programmatically"></a>Программное управление пакетами и папками

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


<a name="top"></a> В процессе программирования при работе с пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может возникнуть необходимость определить, существует ли отдельный пакет или папка, либо управлять папками, где хранятся пакеты. Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> из пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет разнообразные методы, выполняющие эти требования.    
    
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> Определение существования пакета или папки    
 Чтобы определить программным способом, существует ли сохраненный пакет, перед попыткой загрузить и выполнить его вызовите один из следующих методов:    
    
|Место хранения|Вызываемый метод|    
|----------------------|--------------------|    
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 Чтобы определить программным способом, существует ли папка, перед попыткой получить список пакетов, хранящихся в этой папке, вызовите один из следующих методов:    
    
|Место хранения|Вызываемый метод|    
|----------------------|--------------------|    
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [Вверх](#top)    
    
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> Управление пакетами и папками    
 Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет дополнительные методы для управления пакетами и папками, в которых эти пакеты хранятся.    
    
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> Удаление пакета    
 Для удаления сохраненного пакета программным способом вызовите один из следующих методов:    
    
|Место хранения|Вызываемый метод|    
|----------------------|--------------------|    
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|    
    
 [Вверх](#top)    
    
###  <a name="creating-a-folder"></a><a name="managing_create"></a> Создание папки    
 Для создания папки хранения программным способом вызовите один из следующих методов:    
    
|Место хранения|Вызываемый метод|    
|----------------------|--------------------|    
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|    
    
 [Вверх](#top)    
    
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> Удаление папки    
 Для удаления папки хранения программным способом вызовите один из следующих методов:    
    
|Место хранения|Вызываемый метод|    
|----------------------|--------------------|    
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|    
    
 [Вверх](#top)    
    
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> Переименование папки    
 Для переименования папки хранения программным способом вызовите один из следующих методов:    
    
|Место хранения|Вызываемый метод|    
|----------------------|--------------------|    
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|    
    
 [Вверх](#top)    
    
## <a name="see-also"></a>См. также:    
 [Управление пакетами (службы SSIS)](../../integration-services/service/package-management-ssis-service.md)     
 [Программное перечисление доступных пакетов](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)    
    
  
