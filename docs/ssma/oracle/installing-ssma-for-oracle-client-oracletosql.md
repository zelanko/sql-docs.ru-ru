---
title: Установка SSMA для клиента Oracle (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: fc295e108357040617bf6bdaa1af61fada2c97ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68259682"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Установка клиента SSMA для Oracle (OracleToSQL)
Клиент SSMA состоит из программных файлов, которые выполняют следующие задачи:  
  
-   Соединение с базой данных Oracle  
  
-   Подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Преобразование объектов базы данных Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в синтаксис.  
  
-   Загрузите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Перенос данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
В этом разделе приведены предварительные требования для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>Предварительные требования  
SSMA предназначен для работы с Oracle 9 или более поздними версиями и всеми выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Перед установкой SSMA убедитесь, что компьютер соответствует следующим требованиям.  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Версия 4,0 или более поздняя [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] . [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версия 4,0 доступна на носителе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] продукта. Его также можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Клиент Oracle 9,0 или более поздней версии, а также подключение к базам данных Oracle, которые требуется перенести. Версия клиента Oracle должна совпадать с версией базы данных Oracle или более поздней версии.  
  
    Вы можете установить клиент Oracle с носителя продукта Oracle или с веб-сайта Oracle. Дополнительные сведения о подключении см. [в разделе Подключение к Oracle Database &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Доступ к и достаточным разрешениям на компьютере, на котором размещен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] целевой экземпляр или база данных SQL Azure, где будут перенесены объекты и данные базы данных. Дополнительные сведения см. [в разделе Подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   рекомендуется 4 ГБ ОЗУ.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Установка клиента SSMA для Oracle  
SSMA можно загрузить из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmafororacle).  
  
После загрузки последней версии необходимо извлечь файлы установки из, прежде чем можно будет установить SSMA.  
  
**Установка клиента SSMA**  
  
1.  Дважды щелкните SSMA для Oracle *n*. Install. exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если предварительные условия не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Убедитесь, что установлены все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки выберите вариант **Обычная**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для Oracle перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft Помощник по миграции SQL Server для Oracle.  
  
Помимо файлов программы SSMA, необходимо также установить пакет SSMA для пакета расширения Oracle на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. [в разделе Install SSMA Components on SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>См. также:  
[Установка компонентов SSMA на SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Перенос баз данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
