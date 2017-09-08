---
title: "Установка SSMA для СУБД Sybase (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 432a31ae12c1d3fc091893de332a72a5da1c4fc3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma--for-sybase-sybasetosql"></a>Установка SSMA для СУБД Sybase (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) для Sybase состоит из клиентского приложения, который позволяет выполнить миграцию из Sybase адаптивной Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Он также содержит пакет расширения, который поддерживает перенос данных и использование системных функций ASE перенесенных баз данных.  
  
Для установки клиентского приложения на компьютере, в котором будет выполнять действия по миграции. Необходимо установить файлы пакета расширения на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для размещения базы данных после миграции.  
  
## <a name="upgrading-ssma-for-sybase"></a>Обновление SSMA для СУБД Sybase  
Если вы хотите обновить до более поздней версии SSMA для СУБД Sybase, необходимо сначала удалить клиента и пакет расширения сервера, а затем установить новую версию.  
  
При открытии проекта из более ранней версии SSMA для СУБД Sybase SSMA запрашивает, если для преобразования проекта до новой версии. Необходимо нажать кнопку **Да** для работы с проектом в новой версии SSMA.  
  
## <a name="contents"></a>Содержание  
  
|Раздел|Description|  
|---------|---------------|  
|[Установка SSMA для клиента Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Предоставляет сведения и инструкции по установке клиента SSMA.|  
|[Установка компонентов SSMA на SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Сведения и инструкции по установке пакета расширения в экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Удаление SSMA для Sybase компоненты &#40; SybaseToSQL &#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Содержит инструкции по удалению клиента пакет программы и расширение.|  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

