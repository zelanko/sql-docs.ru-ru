---
title: "Инструкция SQL Create Table (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
caps.latest.revision: 67
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ad9b68e2a0ac4cd88917a7b45c7a8f12b14f3ab4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>Инструкция SQL Create Table (мастер импорта и экспорта SQL Server)
Если в диалоговом окне **Сопоставления столбцов** последовательно выбрать **Создать целевую таблицу** и **Изменить SQL** , в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется диалоговое окно **Инструкция SQL Create Table** . На этой странице можно просмотреть и при необходимости настроить команду **CREATE TABLE**, запускаемую мастером для создания целевой таблицы.
  
> [!NOTE]
> Если вам нужны сведения об инструкции CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)], а не о диалоговом окне **Инструкция SQL Create Table** мастера импорта и экспорта[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. раздел [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md). 
  
## <a name="screen-shot-of-the-create-table-sql-statement-page"></a>Снимок экрана: страница "Инструкция SQL Create Table"  
 На следующем снимке экрана показано диалоговое окно **Инструкция SQL Create Table** .
 
В этом примере в поле **Инструкции SQL** указана инструкция по умолчанию **CREATE TABLE** , созданная мастером. Эта инструкция создает Новая целевая таблица с именем **Person.AddressNew** , являющийся копией **Person.Address** исходной таблицы. 
  
 ![Создание таблицы страница мастера импорта и экспорта](../../integration-services/import-export-data/media/create-table.png "страницы создания таблицы из мастера импорта и экспорта")  
  
## <a name="review-or-regenerate-the-create-table-statement"></a>Просмотр или повторное формирование инструкции CREATE TABLE  
 **Инструкция SQL**  
Выводит автоматически созданную инструкцию SQL и позволяет редактировать ее.
 
Если вы измените команду CREATE TABLE по умолчанию, также может потребоваться внести изменения в связанный столбец сопоставления после возврата в **сопоставления столбцов** диалоговое окно.  
  
Если в текст инструкции SQL необходимо вставить символ возврата каретки, нажмите клавиши CTRL + ВВОД. При нажатии одной лишь клавиши ВВОД диалоговое окно закрывается.  
  
Дополнительные сведения об инструкции CREATE TABLE и синтаксисе см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).   
  
 **Автоформирование**  
 Восстановить инструкцию SQL по умолчанию, если вы изменили его, щелкнув **автоматическое создание**.  
  
## <a name="create-a-table-that-includes-a-filestream-column"></a>Создание таблицы со столбцом FILESTREAM  
 Мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает инструкцию CREATE TABLE по умолчанию на основе подключенного источника данных. Эта инструкция CREATE TABLE не включает атрибут FILESTREAM, даже если исходная таблица содержит столбец FILESTREAM.
 1.  Чтобы скопировать столбец FILESTREAM с помощью мастера, сначала следует создать хранилище FILESTREAM в целевой базе данных.
 2.  Затем вручную добавьте атрибут FILESTREAM к инструкции CREATE TABLE в диалоговом окне **Инструкция SQL Create Table** .  

Дополнительные сведения о синтаксисе см. в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md). Дополнительные сведения о FILESTREAM см. в разделе [Данные большого двоичного объекта (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
## <a name="whats-next"></a>Дальнейшие действия  
 После просмотра и настройки команды CREATE TABLE и нажатия кнопки **ОК**диалоговое окно **Инструкция SQL Create Table** вернет вас в диалоговое окно **Сопоставления столбцов** . Дополнительные сведения см. в разделе [Сопоставления столбцов](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).
 
 ## <a name="see-also"></a>См. также:
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



