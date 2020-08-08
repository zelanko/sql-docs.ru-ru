---
title: Миграция баз данных Sybase ASE в SQL Server в базе данных SQL Azure | Документация Майкрософт
description: Используйте этот рекомендуемый процесс для переноса адаптивных серверных баз данных SAP в SQL Server или базу данных SQL Azure с помощью Помощник по миграции SQL Server (SSMA).
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: e0a938d615b15dc7b280a6c6b9337a546e0059bf
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934700"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Миграция баз данных SAP ASE в SQL Server — база данных SQL Azure (SybaseToSQL)
Помощник по миграции SQL Server (SSMA) для SAP адаптивного сервера Enterprise (ASE) — это Комплексная среда, которая помогает быстро перенести базы данных SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или. С помощью SSMA для SAP ASE можно просматривать объекты и данные базы данных, оценивать базы данных для миграции, переносить объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure, а затем переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или из нее.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Чтобы успешно перенести объекты и данные из баз данных SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базу данных SQL Azure, используйте следующую процедуру.  
  
1.  [Создайте новый проект SSMA](working-with-ssma-projects-sybasetosql.md).  
  
    После создания проекта можно задать параметры преобразования проекта, миграции и сопоставления типов. Сведения о параметрах проекта см. в разделе [Установка параметров проекта &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Сведения о настройке сопоставлений типов данных см. в разделе [Mapping SYBASE ASE and SQL Server Data types &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Подключитесь к серверу базы данных SAP ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
3.  [Подключитесь к экземпляру SQL Server](connecting-to-sql-server-sybasetosql.md) или [подключитесь к экземпляру базы данных SQL Azure](connecting-to-azure-sql-db-sybasetosql.md).  
  
4.  [Сопоставьте схемы базы данных SAP ASE с SQL Server или схемами базы данных SQL Azure](https://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  При необходимости [Создайте отчеты об оценке](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) для оценки объектов базы данных для преобразования и оценки времени преобразования.  
  
6.  [Преобразуйте схемы базы данных SAP ASE в схемы базы данных SQL SQL Server или Azure](https://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Загрузите преобразованные объекты базы данных в SQL Server или базу данных SQL Azure](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Либо сохраните сценарий и запустите его в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных SQL Azure, либо синхронизируйте объекты базы данных.  
  
8.  [Перенос данных в SQL Server или базу данных SQL Azure](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. При необходимости обновите приложения базы данных.  
  
## <a name="see-also"></a>См. также статью  
[Установка SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Начало работы с SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
