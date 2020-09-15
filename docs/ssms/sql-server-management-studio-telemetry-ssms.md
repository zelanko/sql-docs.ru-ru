---
description: Локальный аудит для сбора данных об использовании и данных диагностики в SSMS
title: Данные об использовании компонентов и данные диагностики
ms.custom: seo-lt-2019
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c26ab977839927751903eead0533256ab91fde2c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88370140"
---
# <a name="local-audit-for-ssms-usage-and-diagnostic-data-collection"></a>Локальный аудит для сбора данных об использовании и данных диагностики в SSMS
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Среда SQL Server Management Studio (SSMS) содержит функции, работающие через Интернет, с помощью которых можно собирать и отправлять в корпорацию Майкрософт анонимные данные об использовании компонентов или данные диагностики. SSMS может собирать стандартные сведения о компьютере, а также сведения об использовании и производительности. Эти данные могут отправляться в корпорацию Майкрософт и использоваться для анализа в целях улучшения качества, безопасности и надежности среды SSMS. Сбор таких сведений, как имена, адреса и другие сведения личного характера, не осуществляется. Дополнительные сведения см. в [заявлении о конфиденциальности Майкрософт](https://privacy.microsoft.com/privacystatement) и [приложении к заявлению о конфиденциальности SQL Server](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="audit-feature-usage-and-diagnostic-data"></a>Аудит данных об использовании компонентов и данных диагностики

Чтобы просмотреть данные об использовании компонентов, собранные SSMS, сделайте следующее:

1.  Запустите среду SSMS.
2.  Щелкните **Просмотр**, а затем выберите в главном меню **Вывод**, чтобы отобразить окно **вывода**. 
3.  Когда появится окно **Вывод**, выберите в меню **Показать выходные данные из:** пункт **Телеметрия**.

Если вы используете SSMS для взаимодействия с базами данных, в окне **Вывод** отображаются собранные данные.

## <a name="enable-or-disable-usage-and-diagnostic-data-collection-in-ssms"></a>Включение и отключение в среде SSMS сбора данных об использовании и данных диагностики

Чтобы согласиться на сбор данных об использовании для SSMS или отказаться от него:

- Для среды SQL Server Management Studio 17:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\14.0`

  Имя RegEntry — `UserFeedbackOptIn`.

  Тип записи — `DWORD`: `0` — отказаться; `1` — согласиться.

  Кроме того, среда SSMS 17.x основана на оболочке Visual Studio 2015, а в экземпляре Visual Studio функция сбора отзывов пользователей включена по умолчанию.  

  Чтобы отключить сбор отзывов пользователей в Visual Studio на отдельных компьютерах, измените значение следующего подраздела реестра на строку `0` — `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn`.

  Например, измените подраздел следующим образом:  
  `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn `=` 0`

  Групповая политика на базе реестра с этими подразделами будет соблюдаться системой сбора данных об использовании и данных диагностики SQL Server 2017.

- Для среды SQL Server Management Studio 18:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\18.0_IsoShell`

  Имя RegEntry — `UserFeedbackOptIn`.

  Тип записи — `DWORD`: `0` — отказаться; `1` — согласиться.

## <a name="see-also"></a>См. также раздел

- [Настройка сбора данных об использовании и данных диагностики для SQL Server](../sql-server/usage-and-diagnostic-data-configuration-for-sql-server.md)
- [Локальный аудит для сбора данных об использовании и данных диагностики SQL Server](https://msdn.microsoft.com/library/mt743085.aspx)
