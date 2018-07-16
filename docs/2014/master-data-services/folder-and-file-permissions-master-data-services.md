---
title: Разрешения для папок и файлов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], file and folder
- folders [Master Data Services]
- files [Master Data Services]
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: 1cee48c465b95598f4bdbcca6f22df2cf623945d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318774"
---
# <a name="folder-and-file-permissions-master-data-services"></a>Разрешения для папок и файлов (службы Master Data Services)
  При установке [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]папки и файлы устанавливаются по указанному для общих компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] пути установки в файловой системе. При использовании пути установки по умолчанию для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] общих компонентов, путь установки для [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] — *диск*: \Program Files\Microsoft SQL Server\120\Master Data Services. Хотя путь установки общих компонентов можно изменить, следует учитывать разрешения, наследуемые от родительской папки, а также явно заданные для [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]разрешения.  
  
## <a name="inherited-permissions"></a>Наследуемые разрешения  
 Папка **Microsoft SQL Server** , папка **Master Data Services** , а также большинство вложенных папок и файлов наследуют разрешения родительской папки, заданной в программе установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Если было выбрано расположение установки по умолчанию, то родительской папкой, от которой наследуются разрешения, будет *диск*:\Program Files. В приведенной далее таблице описаны разрешения по умолчанию для папки **Program Files**.  
  
> [!NOTE]  
>  Если изменить разрешения по умолчанию для **Program Files**или выбрать другое расположение для установки, то папки и файлы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] унаследуют разрешения соответствующей родительской папки, и эти разрешения могут отличаться от приведенных в таблице ниже.  
  
###### <a name="program-files-default-permissions"></a>Разрешения по умолчанию для папки Program Files  
  
|Имя группы или учетной записи|Разрешения|  
|---------------------------|-----------------|  
|CREATOR OWNER|Специальные разрешения|  
|SYSTEM|Специальные разрешения|  
|Администраторы|Специальные разрешения|  
|Пользователи|Чтение и выполнение, Просмотр содержимого папки, Чтение|  
|TrustedInstaller|Просмотр содержимого папки, Специальные разрешения|  
  
## <a name="explicit-permissions"></a>Явные разрешения  
 Папка **MDSTempDir** и файл [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config (в папке **WebApplication** ) не наследуют разрешения. Для них разрешения задаются явно при установке [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], независимо от выбранного пути установки. Изменять эти разрешения не следует.  
  
###### <a name="mdstempdir-permissions"></a>Разрешения MDSTempDir  
  
|Имя группы или учетной записи|Разрешения|  
|---------------------------|-----------------|  
|SYSTEM|Изменение, Чтение и выполнение, Просмотр содержимого папки, Чтение, Запись|  
|Администраторы|Изменение, Чтение и выполнение, Просмотр содержимого папки, Чтение, Запись|  
|MDS_ServiceAccounts|Изменение, Чтение и выполнение, Просмотр содержимого папки, Чтение, Запись|  
  
###### <a name="webconfig-permissions"></a>Разрешения Web.config  
  
|Имя группы или учетной записи|Разрешения|  
|---------------------------|-----------------|  
|SYSTEM|Полный доступ, Изменение, Чтение и выполнение, Чтение, Запись|  
|Администраторы|Полный доступ, Изменение, Чтение и выполнение, Чтение, Запись|  
|MDS_ServiceAccounts|Чтение и выполнение, Чтение|  
  
 Дополнительные сведения о содержимом файла [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config см. в разделе [Раздел "Веб-конфигурация" (службы Master Data Services)](web-configuration-reference-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](install-windows/install-master-data-services.md)  
  
  
