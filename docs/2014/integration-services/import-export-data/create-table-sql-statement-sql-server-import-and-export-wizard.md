---
title: Инструкция SQL Create Table (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f541ad24e87bf5bdea9ed8b8c2523a73c81daa9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62768006"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>Инструкция SQL Create Table (мастер импорта и экспорта SQL Server)
  Используйте диалоговое окно **инструкция SQL CREATE TABLE** , чтобы просмотреть инструкцию, которая была создана автоматически, или изменить ее в целях. При изменении этой инструкции можно также сделать соответствующие изменения в сопоставлении столбцов, после чего будет необходимо вручную обрабатывать измененную инструкцию SQL.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] формируют инструкцию по умолчанию CREATE TABLE на основании подключенных источников данных. Эта инструкция CREATE TABLE не включает атрибут FILESTREAM, даже если исходная таблица содержит столбец, для которого объявлен атрибут FILESTREAM. Чтобы запустить компонент служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с атрибутом FILESTREAM, сначала следует создать хранилище FILESTREAM в целевой базе данных. Затем добавьте атрибут FILESTREAM к инструкции CREATE TABLE в диалоговом окне **Создание таблицы** . Дополнительные сведения см. в разделе [Данные большого двоичного объекта (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Мастер импорта и экспорта SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Дополнительные сведения о параметрах запуска мастера, а также о разрешениях, необходимых для успешного запуска мастера, см. в разделе [Запуск мастера импорта и экспорта SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 Назначение мастера импорта и экспорта SQL Server заключается в копировании данных из исходного расположения в целевое. Этот мастер может также создать целевую базу данных и целевые таблицы. Однако если нужно скопировать несколько баз данных, таблиц или других объектов базы данных, следует использовать мастер копирования баз данных. Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Параметры  
 **Инструкция SQL**  
 Выводит автоматически созданную инструкцию SQL и позволяет редактировать ее.  
  
> [!NOTE]  
>  Если в конце инструкции SQL необходимо вставить символ возврата каретки, нажмите клавиши CTRL+ВВОД. При нажатии одной лишь клавиши ВВОД диалоговое окно закрывается.  
  
 **Autogenerate (Создавать автоматически)**  
 Если инструкция SQL по умолчанию была изменена, ее можно вернуть к исходному виду, нажав кнопку **Автоформирование**.  
  
  
