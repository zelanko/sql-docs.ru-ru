---
title: Импорт пакета управления SCOM
description: Выполните следующие действия, чтобы импортировать пакеты управления System Center Operations Manager (SCOM) для системы аналитики (ТД). Пакеты управления необходимы для мониторинга параллельного хранилища данных из SCOM.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: bcb0e667424767fd53a5fc7e027e84d512022203
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401084"
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>Импорт пакета управления SCOM — система платформы аналитики
Выполните следующие действия, чтобы импортировать пакеты управления System Center Operations Manager (SCOM) для системы аналитики (ТД). Пакеты управления необходимы для мониторинга параллельного хранилища данных из SCOM. 
  
## <a name="BeforeBegin"></a>Перед началом  
**Необходимые компоненты**  
  
Необходимо установить и запустить System Center Operations Manager 2007 R2.  
  
Пакеты управления должны быть установлены. См. статью [Установка пакетов управления SCOM &#40;Analytics Platform System&#41;](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>Шаг 1. импорт базового пакета управления для устройства SQL Server  
  
1.  Войдите в систему на компьютере, используя учетную запись, которая является членом роли "Администраторы Operations Manager" для группы управления Operations Manager 2007.  
  
2.  В консоли управления нажмите кнопку **Администрирование**.  
  
3.  Щелкните правой кнопкой мыши узел **пакеты управления** и выберите пункт **Импорт пакетов управления**.  
  
    ![Щелкните «Импорт пакетов управления»](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM_IMP")  
  
4.  В списке пакетов управления выберите пакет управления, который необходимо импортировать, нажмите кнопку **выбрать**, а затем нажмите кнопку **Добавить**.  
  
    ![Список пакетов управления](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Выполните поиск **устройства** , а затем выполните детализацию в SQL Server базовое устройство, а затем щелкните **Добавить** два варианта.  
  
    ![База устройства SQL Server](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  Когда два пакета управления находились в нижней выбранной области, нажмите кнопку **ОК**.  
  
    ![Выберите оба пакета управления](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Нажмите кнопку **Установить**.  
  
    ![Нажмите "Установить".](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  После завершения нажмите кнопку **Закрыть**.  
  
    ![После завершения нажмите кнопку Закрыть.](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Импорт пакета мониторинга для устройства параллельного хранилища данных Microsoft SQL Server 2008 R2  
  
1.  Щелкните правой кнопкой мыши узел **пакеты управления** и выберите пункт **Импорт пакетов управления**.  
  
2.  Выберите **Добавить с диска**....  
  
    ![Щелкните правой кнопкой мыши пакеты управления](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Перейдите в папку, куда были извлечены пакеты управления SQL Server PDW и выберите три пакета управления в разделе "выбранные пакеты управления для импорта". Это можно сделать, выбрав первый элемент, нажав клавишу Shift и выбрав последнюю из них. Как только они будут выбраны, нажмите кнопку **Открыть**.  
  
    ![Выберите пакеты управления](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Нажмите кнопку **Установить**.  
  
    ![Нажмите "Установить".](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Нажмите кнопку **Закрыть**.  
  
    ![Нажмите кнопку Закрыть.](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Дальнейшее действие  
Теперь, когда пакеты управления импортированы, перейдите к следующему шагу: [Настройка SCOM для мониторинга системы аналитики платформа &#40;Analytics Platform system&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
