---
title: Среда SQL Server Management Studio. Телеметрия (SSMS) | Документация Майкрософт
ms.custom: ''
ms.date: 02/20/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce4abde855b5fe6a65c3038e93eb8609f9736dc1
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59240392"
---
# <a name="local-audit-for-ssms-usage-and-diagnostic-data-collection"></a>Локальный аудит для сбора данных об использовании и данных диагностики в SSMS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Среда SQL Server Management Studio (SSMS) содержит функции, работающие через Интернет, с помощью которых можно собирать и отправлять в корпорацию Майкрософт анонимные данные об использовании компонентов или данные диагностики. SSMS может собирать стандартные сведения о компьютере, а также сведения об использовании и производительности. Эти данные могут отправляться в корпорацию Майкрософт и использоваться для анализа в целях улучшения качества, безопасности и надежности среды SSMS. Сбор таких сведений, как имена, адреса и другие сведения личного характера, не осуществляется. Дополнительные сведения см. в [заявлении о конфиденциальности Майкрософт](https://privacy.microsoft.com/privacystatement) и [приложении к заявлению о конфиденциальности SQL Server](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="audit-feature-usage-data"></a>Данные об использовании компонентов для аудита

Чтобы просмотреть данные об использовании компонентов, собранные SSMS, сделайте следующее:
1.  Запустите среду SSMS.
2.  Щелкните **Просмотр**, а затем выберите в главном меню **Вывод**, чтобы отобразить окно **вывода**. 
3.  Когда появится окно **Вывод**, выберите в меню **Показать выходные данные из:** пункт **Телеметрия**.

Если вы используете SSMS для взаимодействия с базами данных, в окне **Вывод** отображаются собранные данные.

## <a name="enable-or-disable-usage-feedback-collection-in-ssms"></a>Включение и отключение в среде SSMS сбора информации об использовании

Чтобы согласиться на сбор данных об использовании для SSMS или отказаться от него:

- Для среды SQL Server Management Studio 17:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\14.0`

  Имя RegEntry = `UserFeedbackOptIn`

  Тип записи — `DWORD`: `0` — отказаться; `1` — согласиться.

  Кроме того, среда SSMS 17.x основана на оболочке Visual Studio 2015, а в экземпляре Visual Studio функция сбора отзывов пользователей включена по умолчанию.  

  Чтобы отключить сбор отзывов пользователей в Visual Studio на отдельных компьютерах, измените значение следующего подраздела реестра на строку `0`: `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn`

  Например, измените подраздел следующим образом:  
  `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn `=` 0`

  Групповая политика на базе реестра с этими подразделами будет соблюдаться системой сбора данных об использовании и данных диагностики SQL Server 2017.

- Для среды SQL Server Management Studio 18:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\18.0_IsoShell`

  Имя RegEntry = `UserFeedbackOptIn`

  Тип записи — `DWORD`: `0` — отказаться; `1` — согласиться.

## <a name="see-also"></a>См. также раздел

- [Настройка сбора данных об использовании и данных диагностики для SQL Server](../sql-server/usage-and-diagnostic-data-configuration-for-sql-server.md)
- [Локальный аудит для сбора данных об использовании и данных диагностики SQL Server](http://msdn.microsoft.com/library/mt743085.aspx)
