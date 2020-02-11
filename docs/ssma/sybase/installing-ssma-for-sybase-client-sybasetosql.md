---
title: Установка SSMA для клиента Sybase (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e770c2f2-52b9-4471-a207-0d35df41399c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8680685640b234e47f6e68d7fb802fc7e2f5d81c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029019"
---
# <a name="installing-ssma--for-sybase-client-sybasetosql"></a>Установка клиента SSMA для Sybase (SybaseToSQL)
Клиент SSMA состоит из программных файлов, которые используются для подключения к серверу базы данных адаптивного сервера предприятия (ASE) Sybase, а также к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляру или базе данных SQL Azure, преобразованию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов базы данных ASE в или к синтаксису базы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных SQL Azure, загрузке объектов в или базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure, а затем переносу данных в или Azure sqldb.  
  
В этом разделе приведены предварительные требования для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>Предварительные требования  
SSMA предназначен для работы с ASE 11.9.2 или более поздними версиями и всеми выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Перед установкой SSMA убедитесь, что компьютер соответствует следующим требованиям.  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework версии 4,0 или более поздней версии. .NET Framework версии 4,0 можно найти на носителе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] продукта. Его также можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Поставщик Sybase OLEDB/ADO.Net/ODBC и подключение к серверу базы данных Sybase ASE, содержащему базы данных, которые необходимо перенести. Вы можете установить поставщики из носителя с продуктом Sybase ASE. Дополнительные сведения о подключении см. [в статье подключение к SYBASE ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Доступ к и достаточным разрешениям на компьютере, на котором размещен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] целевой экземпляр или база данных SQL Azure, где будут перенесены объекты и данные базы данных. Дополнительные сведения см. в статьях [Подключение к SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [Подключение к базе данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
-   рекомендуется 4 ГБ ОЗУ.  
  
## <a name="installing-the-ssma-for-sybase-client"></a>Установка клиента SSMA для Sybase  
SSMA можно загрузить из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmaforsybase).  
  
После загрузки последней версии необходимо извлечь файлы установки из, прежде чем можно будет установить SSMA.  
  
**Установка клиента SSMA**  
  
1.  Дважды щелкните SSMA для Sybase *n*. Install. exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если предварительные условия не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Убедитесь, что установлены все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки выберите вариант **Обычная**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для Sybase перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft Помощник по миграции SQL Server для Sybase.  
  
Помимо файлов программы SSMA, необходимо также установить пакет расширений SSMA для Sybase на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. [в разделе Install SSMA Components on SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md).  
  
## <a name="see-also"></a>См. также:  
[Установка компонентов SSMA на SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Миграция баз данных Sybase ASE в SQL Server Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
