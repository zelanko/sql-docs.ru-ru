---
title: "Установка SSMA для клиента Oracle (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
caps.latest.revision: "19"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: 90e1f2b745ef0a093fb7a5b2ebf662aa969154f1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Установка SSMA для клиента Oracle (OracleToSQL)
SSMA клиента состоит из файлов программы, которые выполняют следующие задачи:  
  
-   Соединение с базой данных Oracle  
  
-   Подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Преобразование объектов базы данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксиса.  
  
-   Загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Этот раздел содержит необходимые условия для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>предварительные требования  
SSMA предназначен для работы с Oracle 9 или более поздних версиях, а также всех выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Прежде чем устанавливать SSMA, убедитесь в том, что компьютер соответствует следующим требованиям:  
  
-   Windows 7 или более поздней версии или Windows Server 2008 или более поздних версиях.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 или более поздней версии. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Версии 4.0 можно найти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] установочного носителя. Его можно также получить из [Центр разработчиков .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Клиент Oracle 9.0 или более поздней версии, а подключения к базам данных Oracle, которые требуется перенести. Версия клиента Oracle должен быть той же версии, или более поздней версии, чем версия базы данных Oracle.  
  
    Можно установить клиента Oracle, с носителя продукта Oracle или Oracle веб-сайта. Сведения о подключении см. в разделе [подключение к базе данных Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Доступ к и необходимых разрешений на компьютере, на котором целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базе данных SQL Azure, где можно будет миграция объектов базы данных и данных. Дополнительные сведения см. в разделе [подключение к SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   4 ГБ ОЗУ рекомендуется.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Установка SSMA для клиента Oracle  
SSMA можно загрузить из Интернета. Загрузить последнюю версию [SQL Server Migration Assistant страницы загрузки](http://aka.ms/ssmafororacle).  
  
После загрузки последней версии, нужно извлечь файлы установки из перед установкой SSMA.  
  
**Чтобы установить клиент SSMA**  
  
1.  Дважды щелкните SSMA для Oracle  *n* . Install.exe, где  *n*  — номер сборки.  
  
2.  На странице приветствия нажмите кнопку **Далее**.  
  
    Если у вас установлены необходимые компоненты, появится сообщение, указывающее, необходимо сначала установить необходимые компоненты. Убедитесь, что устанавливать все необходимые компоненты, а затем снова запустите программу установки.  
  
3.  Прочитайте лицензионное соглашение конечного пользователя. Если вы согласны, установите **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4.  На странице Выбор типа установки щелкните **обычные**.  
  
5.  Нажмите кнопку **Установить**.  
  
> [!IMPORTANT]  
> 1.  Удалите все предыдущие версии SSMA для Oracle перед установкой новой версии.  
  
Расположение установки по умолчанию — C:\Program Files\Microsoft SQL Server Migration Assistant для Oracle.  
  
Помимо SSMA программные файлы, необходимо также установить SSMA для пакета расширения Oracle на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [Установка компонентов SSMA на SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>См. также:  
[Установка компонентов SSMA на SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Миграция баз данных Oracle в SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
