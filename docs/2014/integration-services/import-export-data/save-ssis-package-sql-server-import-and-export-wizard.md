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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 690e73e0bda9cac2521cfec3fc6296c50fd3b69a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436811"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server)
  Страница **Сохранение пакета служб SSIS** используется для именования, описания и сохранения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пакета Integration Services ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] ) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` базе данных или в файле с расширением DTSX.  
  
> [!NOTE]  
>  В выпуске [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] пакет, созданный при помощи мастера, сохранить нельзя.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Мастер импорта и экспорта SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Дополнительные сведения о параметрах запуска мастера и о разрешениях, необходимых для успешного запуска мастера, см. [в разделе Запуск мастера импорта и экспорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 Назначение мастера импорта и экспорта SQL Server заключается в копировании данных из исходного расположения в целевое. Этот мастер может также создать целевую базу данных и целевые таблицы. Однако если нужно скопировать несколько баз данных, таблиц или других объектов базы данных, следует использовать мастер копирования баз данных. Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Статические параметры  
 **имя**;  
 Введите уникальное имя пакета.  
  
 **Описание**  
 Введите описание пакета. Рекомендуется описывать пакеты в связи с их предназначением, чтобы пакеты описывали сами себя и их легко было обслуживать.  
  
 **Целевой объект**  
 Просмотрите цель ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или файл), которая ранее была назначена для целевого файла.  
  
## <a name="target-dynamic-options"></a>Целевые динамические параметры  
  
### <a name="target--sql-server"></a>Назначение = SQL Server  
 **Имя сервера**  
 Выбрав цель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], введите или выберите имя целевого сервера.  
  
 **Использовать проверку подлинности Windows**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], укажите, следует ли устанавливать соединение с сервером, используя встроенную проверку подлинности Windows. Предпочтителен этот метод проверки подлинности.  
  
 **Использовать проверку подлинности SQL Server**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], укажите, следует ли устанавливать соединение с сервером, используя проверку подлинности SQL Server.  
  
 **User name**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указав проверку подлинности SQL Server, введите имя пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Пароль**  
 Выбрав целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указав проверку подлинности SQL Server, введите пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="target--file-system"></a>Назначение = Файловая система  
 **Имя файла**  
 Выбрав назначение файла, введите путь к целевому файлу или нажмите кнопку **Обзор** .  
  
 **Обзор**  
 Выбрав назначение файла, перейдите к целевому файлу с помощью диалогового окна **сохранить пакет** .  
  
## <a name="see-also"></a>См. также  
 [Сохранение пакетов](../save-packages.md)  
  
  
