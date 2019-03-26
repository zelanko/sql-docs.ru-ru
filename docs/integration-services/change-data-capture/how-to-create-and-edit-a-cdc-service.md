---
title: Создание и изменение службы CDC Service​ | Документы Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 47d4d2a3e987dada26fddff10c863fa0e3ba3ee8
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58270831"
---
# <a name="how-to-create-and-edit-a-cdc-service"></a>Создание и изменение службы CDC
  В этих процедурах описываются способы создания и изменения службы Oracle CDC Service при помощи консоли конфигурации службы CDC.  
  
 Эту процедуру может выполнять пользователь Windows с правами администратора на компьютере, где настроена служба Oracle CDC.  
  
### <a name="to-create-a-new-cdc-service"></a>Создание службы CDC  
  
1.  В меню **Пуск** выберите **Конфигурация службы CDC для Oracle**.  
  
2.  На панели слева щелкните правой кнопкой мыши «Локальные службы CDC» и выберите команду «Создать службу».  
  
     Можно также щелкнуть **Создать службу** на панели **Действия** .  
  
3.  Введите или укажите требуемые сведения в диалоговом окне «Создание службы Oracle CDC Service». Дополнительные сведения о вводе данных в диалоговое окно «Создание службы Oracle CDC Service» см. в разделе [Create and Edit an Oracle CDC Service](../../integration-services/change-data-capture/create-and-edit-an-oracle-cdc-service.md) .  
  
     Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , указанное в диалоговом окне «Создание службы Oracle CDC Service», используется службой Oracle CDC Service при работе. Этому имени входа достаточно быть членом предопределенной роли сервера public, никаких других прав доступа не требуется. Когда добавляются новые экземпляры Oracle CDC, это имя входа получает доступ **db_owner** к соответствующим базам данных CDC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Введя необходимые данные, нажмите кнопку **OK**.  
  
     Чтобы создать определение службы Windows для Oracle CDC, программе требуется доступ с возможностью обновления к базе данных MSXDBCDC в соответствующем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При нажатии кнопки **OK**появляется диалоговое окно с приглашением ввести имя входа, имеющее доступ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с возможностью обновления к базе данных MSXDBCDC.  
  
     Дополнительные сведения о вводе данных в диалоговое окно «Подключение к SQL Server» см. в разделе [Connection to SQL Server](../../integration-services/change-data-capture/connection-to-sql-server.md).  
  
5.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно «Создание службы Oracle CDC Service».  
  
### <a name="to-edit-a-cdc-service"></a>Изменение службы CDC  
  
1.  В меню **Пуск** выберите **Конфигурация службы CDC для Oracle**.  
  
2.  На панели слева выберите **Локальные службы CDC** , щелкните правой кнопкой мыши локальную службу, которую нужно изменить, и выберите пункт **Свойства**.  
  
     Можно также выбрать нужную службу в списке, расположенном в центре, и щелкнуть **Свойства** на панели **Действия**.  
  
3.  Введите или укажите требуемые сведения в диалоговом окне «Свойства службы CDC». Сведения о вводе данных в диалоговое окно «Свойства службы CDC» см. в разделе [Create and Edit an Oracle CDC Service](../../integration-services/change-data-capture/create-and-edit-an-oracle-cdc-service.md) .  
  
4.  Завершив ввод необходимых данных, нажмите кнопку **OK**. Откроется диалоговое окно «Подключение к SQL Server».  
  
     Если пользователь с именем входа, не имеющим разрешение на запись в базе данных MSXDBDCDC, попытается создать экземпляр Oracle CDC, выводится сообщение об ошибке. Нажмите кнопку **ОК** , чтобы открыть диалоговое окно «Подключение к SQL Server». Введите учетные данные, относящиеся к имени входа, имеющему разрешение на запись в базу данных MSXDBCDC, например учетные данные роли базы данных **db_owner** .  
  
     Дополнительные сведения о вводе данных в диалоговое окно «Подключение к SQL Server» см. в разделе [Connection to SQL Server](../../integration-services/change-data-capture/connection-to-sql-server.md).  
  
5.  Нажмите кнопку **ОК** в диалоговом окне «Подключение к Oracle». Оба диалоговых окна закроются. Служба будет обновлена и зарегистрирована.  
  
## <a name="see-also"></a>См. также:  
 [Конструктор системы отслеживания измененных данных для Oracle компании Attunity](../../integration-services/change-data-capture/change-data-capture-designer-for-oracle-by-attunity.md)   
 [Create and Edit an Oracle CDC Service](../../integration-services/change-data-capture/create-and-edit-an-oracle-cdc-service.md)  
  
  
