---
title: Преобразование типов без проверки (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 01/11/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.nomappingfile.f1
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a6f07634f9f4a3fba48889391a4bfc9e4e245df
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71285328"
---
# <a name="convert-types-without-conversion-checking-sql-server-import-and-export-wizard"></a>Преобразование типов без проверки (мастер импорта и экспорта SQL Server)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  После выбора существующих таблиц и представлений, которые нужно скопировать, или после просмотра своего запроса в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может открыться страница **Преобразование типов без проверки**. Эта страница отображается, если мастеру не удается найти требуемые файлы преобразования и сопоставления типов данных между источником и назначением. На странице содержатся сведения, которые помогут понять, чего не хватает.
  
 Нажмите кнопку **Далее** , чтобы продолжить, не зная о результате преобразований типов данных. В противном случае нажмите кнопку **Назад** , чтобы изменить настройки, или нажмите кнопку **Отмена** , чтобы выйти из мастера.

## <a name="screen-shot-of-the-convert-types-page"></a>Снимок экрана: страница "Преобразование типов"  
  
На следующем снимке экрана показан пример страницы мастера **Преобразование типов без проверки** .

![Преобразование типов](../../integration-services/import-export-data/media/convert-types.png)

Проблема заключается в том, что мастеру не удается найти файл сопоставления, который соотносит типы данных для выбранного назначения.

В данных на этой странице нет имени отсутствующего файла сопоставления. Так как мастер не знает, существует ли файл для указанного поставщика данных, он не может предоставить имя отсутствующего файла.

## <a name="whats-next"></a>Дальнейшие действия  
 Нажмите кнопку **Далее** , чтобы дать согласие на продолжение, не зная о результате преобразований типов данных. Откроется следующая страница — **Сохранение и запуск пакета**. На этой странице можно указать, нужно ли немедленно запустить операцию копирования. В зависимости от конфигурации также можно сохранить пакет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], созданный с помощью мастера, чтобы настроить и использовать его позднее. Дополнительные сведения см. в разделе [Сохранение и запуск пакета](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>См. также раздел
[Сопоставление типов данных в мастере импорта и экспорта SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
