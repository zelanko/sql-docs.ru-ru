---
title: Установка SSMA для SAP ASE (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 91a4dfcf8add3900c51e33a6e40fa874ce9f9798
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028973"
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Установка SSMA для SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции (SSMA) для SAP адаптивного сервера предприятия (ASE) состоит из клиентского приложения, которое используется для миграции из SAP ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или из нее. Он также содержит пакет расширений, который поддерживает перенос данных и использование системных функций ASE в перенесенных базах данных.  
  
Установите клиентское приложение на компьютер, с которого планируется выполнить миграцию. Установите файлы пакета расширения на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] миграция переносимых баз данных.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>Обновление SSMA для SAP ASE  
Если вы хотите выполнить обновление до более поздней версии SSMA для SAP ASE, сначала необходимо удалить клиент и пакет расширений сервера. Затем установите более новую версию.  
  
Если вы откроете проект из более ранней версии SSMA для SAP ASE, SSMA запросит, хотите ли вы преобразовать проект в более новую версию. Нажмите кнопку **Да** , чтобы работать с проектом в более новой версии SSMA.  
  
## <a name="contents"></a>Содержимое  
  
|Статья|Описание|  
|---------|---------------|  
|[Установка SSMA для клиента SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Содержит сведения и инструкции по установке SSMA для клиента SAP ASE.|  
|[Установка компонентов SSMA на SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Содержит сведения и инструкции по установке пакета расширения на экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Удаление SSMA для компонентов SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Содержит инструкции по удалению клиентской программы и пакета расширений.|  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных SAP ASE в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
