---
title: Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 71f0b516b53a7682665c54be4403c5d10a4e5417
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192068"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server)
  Используйте **Сохранение пакета служб SSIS** страницы для имени, описания и сохранить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) пакета [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` базы данных или в файл с расширением dtsx расширение.  
  
> [!NOTE]  
>  В [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], параметр, чтобы сохранить пакет, созданный мастером недоступен.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [SQL Server Импорт и экспорт](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Дополнительные сведения о параметрах запуска этого мастера и о разрешениях, необходимых для успешного запуска мастера см. в разделе [запустить мастер экспорта и импорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 Назначение мастера импорта и экспорта SQL Server заключается в копировании данных из исходного расположения в целевое. Этот мастер может также создать целевую базу данных и целевые таблицы. Однако если нужно скопировать несколько баз данных, таблиц или других объектов базы данных, следует использовать мастер копирования баз данных. Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Название**  
 Введите уникальное имя пакета.  
  
 **Описание**  
 Введите описание пакета. Рекомендуется описывать пакеты в связи с их предназначением, чтобы пакеты описывали сами себя и их легко было обслуживать.  
  
 **Цель**  
 Просмотрите цель ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или файл), был ранее указан для конечного файла.  
  
## <a name="target-dynamic-options"></a>Целевые динамические параметры  
  
### <a name="target--sql-server"></a>Назначение = SQL Server  
 **Имя сервера**  
 Выбрав цель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], введите или выберите имя целевого сервера.  
  
 **Использовать проверку подлинности Windows**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], укажите, следует ли устанавливать соединение с сервером, используя встроенную проверку подлинности Windows. Предпочтителен этот метод проверки подлинности.  
  
 **Использовать проверку подлинности SQL Server**  
 После выбора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения, укажите, следует ли подключиться к серверу с помощью проверки подлинности SQL Server.  
  
 **Имя пользователя**  
 После выбора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения, и указав проверку подлинности SQL Server, введите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя пользователя.  
  
 **Пароль**  
 После выбора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначения, и указав проверку подлинности SQL Server, введите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пароль.  
  
### <a name="target--file-system"></a>Назначение = Файловая система  
 **Имя файла**  
 После выбора назначения файл, введите путь к файлу назначения или используйте **Обзор** кнопки.  
  
 **Обзор**  
 После выбора назначения файл, перейдите к файлу назначения с помощью **Сохранение пакета** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Сохранение пакетов](../save-packages.md)  
  
  