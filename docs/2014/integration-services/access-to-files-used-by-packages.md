---
title: Доступ к файлам, используемым пакетами | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: eed6f09197585e7eb8575c43146ed730497af8a0
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378492"
---
# <a name="access-to-files-used-by-packages"></a>Доступ к файлам, используемым пакетами
  Уровень защиты пакета не способен защитить файлы, хранимые вне пределов пакета. Эти файлы включают в себя:  
  
-   Файлы конфигурации  
  
-   файлы контрольных точек  
  
-   Файлы журналов  
  
 Эти файлы должны быть защищены отдельно, особенно если они содержат конфиденциальные сведения.  
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Если в файле конфигурации хранятся конфиденциальные сведения, такие как данные об имени входа и пароле, то следует сохранить файл в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]или использовать список управления доступом (ACL), чтобы защитить расположение или папку, где хранится этот файл, и разрешить доступ только для определенных учетных записей. Обычно предоставляется доступ для тех учетных записей, которым разрешено запускать пакеты, управлять пакетами и разрешать проблемы, связанные с пакетами, в том числе проверять содержимое файла настройки, контрольные точки и файлы журнала. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] обеспечивает более безопасное хранение, так как предлагает защиту на уровне сервера и базы данных. Чтобы сохранить конфигурации в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], следует использовать тип конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Чтобы сохранить в файловую систему, следует использовать тип конфигурации XML.  
  
 Дополнительные сведения см. в разделах [Конфигурации пакетов](../../2014/integration-services/package-configurations.md), [Создание конфигураций пакетов](../../2014/integration-services/create-package-configurations.md)и [Вопросы безопасности при установке SQL Server](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
## <a name="checkpoint-files"></a>файлы контрольных точек  
 Таким же образом, если используемый пакетом файл контрольных точек содержит конфиденциальные сведения, то следует использовать список управления доступом (ACL) для защиты расположения или папки, где хранится этот файл. Файлы контрольных точек сохраняют данные как о текущем состоянии пакета, так и о текущих значениях переменных. Например, пакет может включать в себя пользовательскую переменную, содержащую номер телефона. Дополнительные сведения см. в разделе [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="log-files"></a>Файлы журналов  
 Записи журнала, сохраненные в файловой системе, также должны быть защищены с использованием списка управления доступом (ACL). Записи журнала также могут храниться в таблицах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и быть защищены системой безопасности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Записи журнала могут содержать конфиденциальные сведения, например если пакет содержит задачу «Выполнение SQL», которая создает инструкцию SQL, ссылающуюся на номер телефона, то запись журнала для инструкции SQL содержит и номер телефона. Инструкция SQL также может раскрыть закрытые данные об именах таблиц и столбцов данных. Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](performance/integration-services-ssis-logging.md).  
  
  
