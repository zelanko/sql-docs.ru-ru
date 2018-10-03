---
title: Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8b8ef62839d7379c35b55af7bcb65ab46e4b455d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048236"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server)
  Используйте **Сохранение пакета служб SSIS** страницы для имени, описания и сохранить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служб Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) пакета [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` базы данных или в файл с расширением dtsx расширение.  
  
> [!NOTE]  
>  В [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], параметр, чтобы сохранить пакет, созданный мастером недоступен.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [SQL Server Импорт и экспорт](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Дополнительные сведения о параметрах запуска этого мастера и о разрешениях, необходимых для успешного запуска мастера, см. в разделе [запустить мастер экспорта и импорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 Назначение мастера импорта и экспорта SQL Server заключается в копировании данных из исходного расположения в целевое. Этот мастер может также создать целевую базу данных и целевые таблицы. Однако если нужно скопировать несколько баз данных, таблиц или других объектов базы данных, следует использовать мастер копирования баз данных. Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Название**  
 Введите уникальное имя пакета.  
  
 **Описание**  
 Введите описание пакета. Рекомендуется описывать пакеты в связи с их предназначением, чтобы пакеты описывали сами себя и их легко было обслуживать.  
  
 **Цель**  
 Просмотрите цель ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или файл), указанное ранее для целевого файла.  
  
## <a name="target-dynamic-options"></a>Целевые динамические параметры  
  
### <a name="target--sql-server"></a>Назначение = SQL Server  
 **Имя сервера**  
 Выбрав цель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], введите или выберите имя целевого сервера.  
  
 **Использовать проверку подлинности Windows**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], укажите, следует ли устанавливать соединение с сервером, используя встроенную проверку подлинности Windows. Предпочтителен этот метод проверки подлинности.  
  
 **Использовать проверку подлинности SQL Server**  
 После выбора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения, укажите, следует ли подключиться к серверу с помощью проверки подлинности SQL Server.  
  
 **Имя пользователя**  
 После выбора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения, и проверка подлинности SQL Server, тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя пользователя.  
  
 **Пароль**  
 После выбора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения, и указав проверку подлинности SQL Server, введите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пароль.  
  
### <a name="target--file-system"></a>Назначение = Файловая система  
 **Имя файла**  
 При выборе целевой файл, введите путь к целевому файлу, или использовать **Обзор** кнопки.  
  
 **Обзор**  
 При выборе целевой файл, перейдите к файлу назначения с помощью **Сохранение пакета** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Сохранение пакетов](../save-packages.md)  
  
  
