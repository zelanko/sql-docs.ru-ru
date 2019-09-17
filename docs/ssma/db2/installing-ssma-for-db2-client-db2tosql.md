---
title: Установка SSMA для клиента DB2 (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 09/07/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1623430eed752db7fa387caf33124082eb318490
ms.sourcegitcommit: 243925311cc952dd455faea3c1156e980959d6de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70774187"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Установка SSMA для клиента DB2 (DB2ToSQL)

Клиент SSMA состоит из программных файлов, которые выполняют следующие задачи:  
  
- Подключитесь к базе данных DB2.  
  
- Подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
- Преобразование объектов базы данных DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в синтаксис.  
  
- Загрузите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
- Перенос данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
В этом разделе приведены предварительные требования для установки и инструкции по установке SSMA.  
  
## <a name="prerequisites"></a>Предварительные требования

SSMA предназначен для работы с DB2 в z/OS версии 9,0 и 10,0 или DB2 на LUW версии 9,8, 10,1 или более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и 2012 или более поздних версиях.  
  
Перед установкой SSMA убедитесь, что компьютер соответствует следующим требованиям.  
  
- Windows 7 или более поздней версии или Windows Server 2008 или более поздней версии.  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Установщик Windows 3,1 или более поздних версий.  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] Версия4,0[!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] или более поздняя. Версия 4,0 доступна [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на носителе продукта. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] Его также можно получить в [центре разработчиков .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
- Поставщик OLEDB (Майкрософт) для DB2 версии 5 или более поздней версии и подключение к базам данных DB2, которые требуется перенести.  
  
- Доступ к и достаточным разрешениям на компьютере, на котором размещен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] целевой экземпляр или база данных SQL Azure, где будут перенесены объекты и данные базы данных. Дополнительные сведения см. [в разделе Подключение к &#40;SQL Server&#41;DB2eToSQL](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
- рекомендуется 4 ГБ ОЗУ.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Поставщик данных OLE DB для DB2 (Майкрософт)  

Чтобы скачать поставщик OLEDB для DB2 версии 6,0, перейдите в раздел [Microsoft® SQL Server® 2017 пакета дополнительных компонентов](https://www.microsoft.com/download/details.aspx?id=55992).

SSMA — это загрузка из Интернета. Чтобы скачать последнюю версию, см. [страницу загрузки помощник по миграции SQL Server](https://aka.ms/ssmafordb2).  
  
После загрузки последней версии извлеките файлы установки, чтобы можно было установить SSMA.  
  
Чтобы установить клиент SSMA, выполните следующие действия.
  
1. Дважды щелкните SSMA для DB2 *n*. Install. exe, где *n* — номер сборки.  
  
2. На странице **приветствия** нажмите кнопку **Далее**.  
  
   Если предварительные условия не установлены, появится сообщение о том, что необходимо сначала установить необходимые компоненты. Убедитесь, что установлены все необходимые компоненты, а затем снова запустите программу установки.  
  
3. Прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения**, а затем нажмите кнопку **Далее**.  
  
4. На странице **Выбор типа установки** выберите вариант **Обычная**.  
  
5. Выберите пункт **Установить**.  
  
> [!IMPORTANT]  
> Удалите все предыдущие версии SSMA для DB2 перед установкой новой версии.
  
Расположение установки по умолчанию — C:\Program Files\Microsoft Помощник по миграции SQL Server для DB2.  
  
## <a name="see-also"></a>См. также

[Установка компонентов SSMA на SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Перенос баз данных DB2 в &#40;SQL Server DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
