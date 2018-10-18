---
title: 架構方法-無伺服器應用程式
description: 簡介架構方法建置雲端式企業應用程式，從無伺服器的多層式架構。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 21e191f17e7d0b4f2d64454fb14c46a4831a8375
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "49369779"
---
# <a name="architecture-approaches"></a><span data-ttu-id="36652-103">架構方法</span><span class="sxs-lookup"><span data-stu-id="36652-103">Architecture approaches</span></span>

<span data-ttu-id="36652-104">了解現有架構的企業應用程式的方法可協助釐清無伺服器所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="36652-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="36652-105">有許多方法和模式，歷經數十年的軟體開發中，而且全都有其自己的優缺點。</span><span class="sxs-lookup"><span data-stu-id="36652-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="36652-106">在許多情況下，根本解決方案不可能會決定單一方法中，但可能整合數種方法也一樣。</span><span class="sxs-lookup"><span data-stu-id="36652-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="36652-107">移轉案例通常涉及從一個架構的方法轉移到另一個透過混合式方法。</span><span class="sxs-lookup"><span data-stu-id="36652-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="36652-108">本章提供企業應用程式的這兩個邏輯與實體架構模式概觀。</span><span class="sxs-lookup"><span data-stu-id="36652-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="36652-109">架構模式</span><span class="sxs-lookup"><span data-stu-id="36652-109">Architecture patterns</span></span>

<span data-ttu-id="36652-110">新式商務應用程式依照各種不同的架構模式。</span><span class="sxs-lookup"><span data-stu-id="36652-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="36652-111">這個區段表示常見模式的介紹。</span><span class="sxs-lookup"><span data-stu-id="36652-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="36652-112">此處所列的模式不一定是所有最佳作法，但說明不同的方法。</span><span class="sxs-lookup"><span data-stu-id="36652-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="36652-113">如需詳細資訊，請參閱 < [Azure 應用程式架構指南](https://docs.microsoft.com/azure/architecture/guide/)。</span><span class="sxs-lookup"><span data-stu-id="36652-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="36652-114">單一的體系</span><span class="sxs-lookup"><span data-stu-id="36652-114">Monoliths</span></span>

<span data-ttu-id="36652-115">許多商務應用程式遵循單體模式。</span><span class="sxs-lookup"><span data-stu-id="36652-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="36652-116">舊版應用程式通常會實作為單一的體系中。</span><span class="sxs-lookup"><span data-stu-id="36652-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="36652-117">在單體模式中，所有的應用程式考量都包含在單一部署中。</span><span class="sxs-lookup"><span data-stu-id="36652-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="36652-118">從資料庫呼叫的使用者介面的所有項目會包含在相同的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="36652-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![單體架構](./media/monolith-architecture.png)

<span data-ttu-id="36652-120">有數個優點單體方法。</span><span class="sxs-lookup"><span data-stu-id="36652-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="36652-121">通常很容易提取的單一程式碼基底，並開始運作。</span><span class="sxs-lookup"><span data-stu-id="36652-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="36652-122">加快時間可能更少，並建立測試環境很簡單，只要提供新的複本。</span><span class="sxs-lookup"><span data-stu-id="36652-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="36652-123">單體可能會設計成包含多個元件和應用程式。</span><span class="sxs-lookup"><span data-stu-id="36652-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="36652-124">不幸的是，單體模式會容易大規模細分。</span><span class="sxs-lookup"><span data-stu-id="36652-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="36652-125">單體方法的主要缺點包括：</span><span class="sxs-lookup"><span data-stu-id="36652-125">Major disadvantages of the monolith approach include:</span></span>

* <span data-ttu-id="36652-126">不能在相同的程式碼基底中的平行處理。</span><span class="sxs-lookup"><span data-stu-id="36652-126">Difficult to work in parallel in the same code base.</span></span>
* <span data-ttu-id="36652-127">任何變更，無論方式一般，都需要部署新的版本，或是整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="36652-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
* <span data-ttu-id="36652-128">重構可能會影響整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="36652-128">Refactoring potentially impacts the entire application.</span></span>
* <span data-ttu-id="36652-129">調整規模的唯一解決方案通常是建立多個，單體的耗用大量資源的副本。</span><span class="sxs-lookup"><span data-stu-id="36652-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
* <span data-ttu-id="36652-130">展開 系統或其他系統取得時，整合可能很困難。</span><span class="sxs-lookup"><span data-stu-id="36652-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
* <span data-ttu-id="36652-131">它可能很難測試，因為需要設定整個單體。</span><span class="sxs-lookup"><span data-stu-id="36652-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
* <span data-ttu-id="36652-132">重複使用程式碼是一項挑戰，並通常其他應用程式最後會有自己的程式碼的複本。</span><span class="sxs-lookup"><span data-stu-id="36652-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="36652-133">許多企業在雲端尋找可移轉單體應用程式，並在同一時間將它們重構到更多可用的模式的機會。</span><span class="sxs-lookup"><span data-stu-id="36652-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="36652-134">通常會劃分為個別的應用程式和元件，以允許這些維護、 部署，而且個別調整。</span><span class="sxs-lookup"><span data-stu-id="36652-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="36652-135">N 層應用程式</span><span class="sxs-lookup"><span data-stu-id="36652-135">N-Layer applications</span></span>

<span data-ttu-id="36652-136">N 層應用程式磁碟分割成特定的層級的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="36652-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="36652-137">最常見的層級包括：</span><span class="sxs-lookup"><span data-stu-id="36652-137">The most common layers include:</span></span>

* <span data-ttu-id="36652-138">使用者介面</span><span class="sxs-lookup"><span data-stu-id="36652-138">User interface</span></span>
* <span data-ttu-id="36652-139">商務邏輯</span><span class="sxs-lookup"><span data-stu-id="36652-139">Business logic</span></span>
* <span data-ttu-id="36652-140">資料存取</span><span class="sxs-lookup"><span data-stu-id="36652-140">Data access</span></span>

<span data-ttu-id="36652-141">中介軟體、 批次處理及 API，可能包含其他層級。</span><span class="sxs-lookup"><span data-stu-id="36652-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="36652-142">請務必注意這些層為邏輯。</span><span class="sxs-lookup"><span data-stu-id="36652-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="36652-143">雖然他們正在開發中隔離，它們可能全部會部署到相同的目標平台。</span><span class="sxs-lookup"><span data-stu-id="36652-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N 層架構](./media/n-layer-architecture.png)

<span data-ttu-id="36652-145">有數個優點，N 層方法，包括：</span><span class="sxs-lookup"><span data-stu-id="36652-145">There are several advantages to the N-Layer approach, including:</span></span>

* <span data-ttu-id="36652-146">重構是隔離至圖層。</span><span class="sxs-lookup"><span data-stu-id="36652-146">Refactoring is isolated to a layer.</span></span>
* <span data-ttu-id="36652-147">小組獨立可以建置、 測試、 部署及維護個別的圖層。</span><span class="sxs-lookup"><span data-stu-id="36652-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
* <span data-ttu-id="36652-148">圖層可以空出，例如資料層時，可能不需要變更 UI 層存取多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="36652-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="36652-149">無伺服器可能會用來實作一個或多個層中。</span><span class="sxs-lookup"><span data-stu-id="36652-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="36652-150">微服務</span><span class="sxs-lookup"><span data-stu-id="36652-150">Microservices</span></span>

<span data-ttu-id="36652-151">**[微服務](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** 架構包含一般的特性，包括：</span><span class="sxs-lookup"><span data-stu-id="36652-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

* <span data-ttu-id="36652-152">應用程式是由數個小型服務所組成。</span><span class="sxs-lookup"><span data-stu-id="36652-152">Applications are composed of several small services.</span></span>
* <span data-ttu-id="36652-153">每個服務會在自己的處理序執行。</span><span class="sxs-lookup"><span data-stu-id="36652-153">Each service runs in its own process.</span></span>
* <span data-ttu-id="36652-154">服務會解決商務網域對齊。</span><span class="sxs-lookup"><span data-stu-id="36652-154">Services are aligned around business domains.</span></span>
* <span data-ttu-id="36652-155">服務會透過輕量型的 Api，通常做為傳輸會使用 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="36652-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
* <span data-ttu-id="36652-156">服務可以部署並獨立升級。</span><span class="sxs-lookup"><span data-stu-id="36652-156">Services can be deployed and upgraded independently.</span></span>
* <span data-ttu-id="36652-157">服務不相依於單一資料存放區。</span><span class="sxs-lookup"><span data-stu-id="36652-157">Services aren't dependent on a single data store.</span></span>
* <span data-ttu-id="36652-158">在系統設計納入考量，失敗，即使特定服務失敗，仍可能會執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="36652-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="36652-159">微服務不一定要以其他架構方法互斥。</span><span class="sxs-lookup"><span data-stu-id="36652-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="36652-160">比方說，多層式架構可以用於中介層使用微服務。</span><span class="sxs-lookup"><span data-stu-id="36652-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="36652-161">它也可在各種不同的方式，從容器的 IIS 主機上的虛擬目錄中實作微服務。</span><span class="sxs-lookup"><span data-stu-id="36652-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="36652-162">微服務的特性可讓它們特別適用於無伺服器的實作。</span><span class="sxs-lookup"><span data-stu-id="36652-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![微服務架構](./media/microservices-architecture.png)

<span data-ttu-id="36652-164">微服務架構的優點包括：</span><span class="sxs-lookup"><span data-stu-id="36652-164">The pros of microservices architectures include:</span></span>

* <span data-ttu-id="36652-165">重構通常是隔離至單一的服務。</span><span class="sxs-lookup"><span data-stu-id="36652-165">Refactoring is often isolated to a single service.</span></span>
* <span data-ttu-id="36652-166">服務可以獨立升級。</span><span class="sxs-lookup"><span data-stu-id="36652-166">Services can be upgraded independently of each other.</span></span>
* <span data-ttu-id="36652-167">可以微調恢復功能和彈性，以個別服務的需求。</span><span class="sxs-lookup"><span data-stu-id="36652-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
* <span data-ttu-id="36652-168">開發情形以平行方式跨不同的小組與平台。</span><span class="sxs-lookup"><span data-stu-id="36652-168">Development can happen in parallel across disparate teams and platforms.</span></span>
* <span data-ttu-id="36652-169">很容易撰寫的外掛式服務的完整測試。</span><span class="sxs-lookup"><span data-stu-id="36652-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="36652-170">微服務隨附自己的挑戰，包括：</span><span class="sxs-lookup"><span data-stu-id="36652-170">Microservices come with their own challenges, including:</span></span>

* <span data-ttu-id="36652-171">判斷所提供的服務，以及如何呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="36652-171">Determining what services are available and how to call them.</span></span>
* <span data-ttu-id="36652-172">管理服務的生命週期。</span><span class="sxs-lookup"><span data-stu-id="36652-172">Managing the lifecycle of services.</span></span>
* <span data-ttu-id="36652-173">了解服務放在一起的整體應用程式中。</span><span class="sxs-lookup"><span data-stu-id="36652-173">Understanding how services fit together in the overall application.</span></span>
* <span data-ttu-id="36652-174">完整的系統測試的跨不同的服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="36652-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="36652-175">最終有解決方案，以解決所有這些挑戰，包括一下使用稍後討論的無伺服器的優點。</span><span class="sxs-lookup"><span data-stu-id="36652-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="36652-176">[上一頁](index.md)
[下一頁](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="36652-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>