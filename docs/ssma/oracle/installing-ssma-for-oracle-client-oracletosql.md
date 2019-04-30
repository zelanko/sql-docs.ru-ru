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
manager: v-thobro
ms.openlocfilehash: 27e5c0ef0c834806351bda73eb69dbe783d78db2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63223580"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Установка клиента SSMA для Oracle (OracleToSQL)
SSMA клиента состоит из программных файлов, которые выполняют следующие задачи:  
  
-   Соединение с базой данных Oracle  
  
-   Подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Преобразование объектов базы данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] синтаксис.  
  
-   Загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Здесь приведены предварительные требования для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA предназначен для работы с Oracle 9 и более поздних версиях все выпуски [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Перед установкой SSMA, убедитесь, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздних версиях или Windows Server 2008 или более поздних версий.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 или более поздней версии. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установочного носителя. Можно также получить его из [Центр разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Клиент Oracle 9.0 или более поздней версии и подключения к базам данных Oracle, которые требуется перенести. Версия клиента Oracle должен быть той же версии или более поздней версии, чем версия базы данных Oracle.  
  
    Клиент Oracle можно установить с носителя продукта Oracle или Oracle веб-узле. Сведения о подключениях см. в разделе [подключение к базе данных Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Доступ к и необходимыми разрешениями на компьютере, на котором размещена на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базе данных SQL Azure, где вам необходимо перенести объекты базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Установка SSMA для клиента Oracle  
SSMA можно загрузить из Интернета. Чтобы загрузить последнюю версию, см. в разделе [SQL Server Migration Assistant страницу загрузки](https://aka.ms/ssmafororacle).  
  
После загрузки последней версии, необходимо извлечь установочные файлы от перед установкой SSMA.  
  
**Установка клиента SSMA**  
  
1.  Дважды щелкните SSMA для Oracle *n*. Install.exe, где *n* — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, что сначала необходимо установить необходимые компоненты. Убедитесь, что вы установили все необходимые компоненты и затем снова запустите программу установки.  
  
3.  Прочтите лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице "Выбор типа установки" нажмите кнопку **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для Oracle перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для Oracle.  
  
В дополнение к файлам программы SSMA, необходимо также установить SSMA для Oracle пакет расширений на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Установка компонентов SSMA в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>См. также  
[Установка компонентов SSMA в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Переход с Oracle баз данных в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
