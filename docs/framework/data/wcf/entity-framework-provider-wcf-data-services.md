---
title: Entity Framework 提供者 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: a09c81b2d0f052884e8e54c899653a6f0e038aff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765618"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework 提供者 (WCF 資料服務)
如同 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 一般，ADO.NET Entity Framework 是以實體資料模型為基礎 (實體資料模型是一種實體關聯模型)。 Entity Framework 會將轉譯作業對實體資料模型，也就所謂的其實作*概念模型*，成針對資料來源的對等作業。 因此，Entity Framework 非常適合做為以關聯式資料為基礎之資料服務的提供者，而且只要資料庫具有支援 Entity Framework 的資料提供者，皆可與 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 搭配使用。 如需目前支援 Entity Framework 的資料來源的清單，請參閱 < [Entity Framework 的協力廠商提供者](https://go.microsoft.com/fwlink/?LinkId=143699)。  
  
 在概念模型中，實體容器是服務的根。 您必須先在 Entity Framework 中定義概念模型，資料服務才能公開資料。 如需詳細資訊，請參閱[如何：建立使用 ADO.NET Entity Framework 資料來源的資料服務](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支援開放式並行存取模型，可讓您定義實體的並行語彙基元。 這個並行語彙基元包含實體的一個或多個屬性，資料服務會使用它來判斷正在要求、更新或刪除的資料中是否已經發生變更。 當取自要求中 eTag 的語彙基元值與目前實體的值不同時，資料服務就會引發例外狀況。 為了指示屬性 (Property) 為並行語彙基元的一部分，您必須在 `ConcurrencyMode="Fixed"` 提供者所定義的資料模型中套用 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 屬性 (Attribute)。 並行語彙基元不得包含索引鍵屬性或導覽屬性。 如需詳細資訊，請參閱 <<c0> [ 更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
 若要深入了解 Entity Framework，請參閱[Entity Framework 概觀](../../../../docs/framework/data/adonet/ef/overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [反映提供者](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
