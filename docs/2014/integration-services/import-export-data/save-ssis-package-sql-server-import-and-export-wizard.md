---
title: Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6af26cafd4f8dd9bf874ae7860c4f796bef48ae1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892771"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server)
  Используйте **Сохранение пакета служб SSIS** страницы для имени, описания и сохранить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служб Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) пакета [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` базы данных или в файл с расширением dtsx расширение.  
  
> [!NOTE]  
>  В выпуске [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] пакет, созданный при помощи мастера, сохранить нельзя.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Мастер импорта и экспорта SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Дополнительные сведения о параметрах запуска этого мастера и о разрешениях, необходимых для успешного запуска мастера, см. в разделе [запустить мастер экспорта и импорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 Назначение мастера импорта и экспорта SQL Server заключается в копировании данных из исходного расположения в целевое. Этот мастер может также создать целевую базу данных и целевые таблицы. Однако если нужно скопировать несколько баз данных, таблиц или других объектов базы данных, следует использовать мастер копирования баз данных. Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Статические параметры  
 **Name**  
 Введите уникальное имя пакета.  
  
 **Описание**  
 Введите описание пакета. Рекомендуется описывать пакеты в связи с их предназначением, чтобы пакеты описывали сами себя и их легко было обслуживать.  
  
 **Цель**  
 Просмотрите цель ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или файл), которая ранее была назначена для целевого файла.  
  
## <a name="target-dynamic-options"></a>Целевые динамические параметры  
  
### <a name="target--sql-server"></a>Назначение = SQL Server  
 **Имя сервера**  
 Выбрав цель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], введите или выберите имя целевого сервера.  
  
 **Использовать проверку подлинности Windows**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], укажите, следует ли устанавливать соединение с сервером, используя встроенную проверку подлинности Windows. Предпочтителен этот метод проверки подлинности.  
  
 **Использовать проверку подлинности SQL Server**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], укажите, следует ли устанавливать соединение с сервером, используя проверку подлинности SQL Server.  
  
 **Имя пользователя**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указав проверку подлинности SQL Server, введите имя пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Пароль**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указав проверку подлинности SQL Server, введите пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="target--file-system"></a>Назначение = Файловая система  
 **Имя файла**  
 При выборе целевой файл, введите путь к целевому файлу, или использовать **Обзор** кнопки.  
  
 **Обзор**  
 При выборе целевой файл, перейдите к файлу назначения с помощью **Сохранение пакета** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Сохранение пакетов](../save-packages.md)  
  
  
