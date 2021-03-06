---
layout: post
title:  "新型冠状病毒，社会与你——数据科学家的视角"
date:   2020-02-10 23:00:00 +0800
categories: update
---

>翻译：[Covid-19, your community, and you — a data science perspective](https://www.fast.ai/2020/03/09/coronavirus/)

>作者：Jeremy Howard 和 Rachel Thomas

>翻译：杨文翔

> 我们是数据科学家，也就是说，我们的工作是了解如何分析和解释数据。当我们分析和新型冠状病毒（新冠病毒）有关的数据时，我们非常担心。社会上最脆弱的部分，老年人和穷人，处于最大的风险之中，但是控制疾病的传播和影响要求我们所有人改变自己的行为。定期彻底洗手，远离人群，取消活动，并且请勿触摸脸部。在这篇文章中，我们解释了我们为什么要关注，您也应该关注。有关您需要了解的关键信息的出色总结，请阅读Ethan Alley（开发非营利性组织以降低流行病风险的技术的总裁）的 [Corona in Brief](https://docs.google.com/document/u/1/d/1vumYWoiV7NlVoc27rMQvmVkVu5cOAbnaW_RKkq2RMaQ/mobilebasic?fbclid=IwAR0If1zzDDldgAy3DZmFhaxAmP046-dwAE_LCj3l9su2XLYpZe2By8mCj1A)。

## 我们亟需一个有效的医疗系统
就在2年前，我们中的一个成员（瑞秋）感染了脑部疾病，这种死亡率的死亡率大约1/4，并使1/3的人得上永久性认知障碍。许多其他人最终会永久性视力和听力受损。瑞秋爬过医院停车场时感到很疯狂。她很幸运能够得到及时的护理，诊断和治疗。直到事件发生前不久，瑞秋身体状况良好。迅速进入急诊室几乎可以肯定挽救了她的生命。

现在，让我们讨论一下新冠病毒，以及在未来几周和几个月内，处于瑞秋这样的局势中的人们可能会发生什么。发现感染新冠病毒的人数每3至6天翻一番。以三天的速度增加一倍，这意味着发现被感染的人数可以在三周内增加100倍（实际上并不是那么简单，但是不要被技术细节所分散）。十分之一的感染者需要住院治疗数周，其中大多数需要氧气。尽管这种病毒还处于初期，但已经有一些地区的医院完全被超支，人们不再能够获得所需的治疗（不仅针对新冠病毒，而且还针对其他任何疾病，例如Rachel所需要的拯救生命的护理）。例如，在一周前的意大利官员说一切都很好的情况下，现在已经有1600万人被封锁（更新：发布此消息后6个小时，意大利将整个国家封锁），并建立了这样的帐篷来帮助患者涌入：

![意大利使用的医疗帐篷](https://www.fast.ai/images/coronavirus/image1.jpeg)
意大利重灾区的区域危机应对部门负责人Antonio Pesenti博士[说](https://www.reuters.com/article/us-health-coronavirus-italy/alarmed-italy-locks-down-north-to-prevent-spread-of-coronavirus-idUSKBN20V06R)：“我们现在被迫在走廊、手术室、恢复室等地方设置紧急监护室。伦巴第是世界上最好的卫生系统之一，而今距崩溃只有一步之遥。”

## 冠状病毒和流感是不同的
流感的死亡率约为感染的0.1％。哈佛大学传染病动力学中心主任马克·利普西奇（Marc Lipsitch）[估计](https://www.washingtonpost.com/opinions/2020/03/06/why-its-so-hard-pin-down-risk-dying-coronavirus/)，对于新冠病毒，这一比例为1-2％。最新的[流行病学模型](https://www.medrxiv.org/content/10.1101/2020.03.04.20031104v1.full.pdf)发现，2月份中国的死亡率为1.6％，比流感高出16倍（但是，这可能是一个相当保守的数字，因为当医疗系统无法应对时，患病率会大大提高）。根据目前的最佳估计，新冠病毒造成的死亡人数今年将比流感多10倍（而且Airbnb前数据科学总监[Elena Grewal进行的建模](https://docs.google.com/spreadsheets/d/1ktSfdDrX_uJsdM08azBflVOm4Z5ZVE75nA0lGygNgaA/edit?usp=sharing)显示，在最坏的情况下，死亡人数可能会多100倍）。这还尚未考虑前面所描述的对医疗系统的巨大影响。可以理解有些人试图说服自己这不是什么新东西，就像流感一样的疾病，因为接受一个根本不熟悉的现实是非常不容易的。

理解被感染人数的指数型增长并不是我们的大脑的直觉擅长的。因此，我们必须以科学家的身份对此进行分析，而不是凭直觉。

![2周后会涨到多少？ 2个月后呢？](https://www.fast.ai/images/coronavirus/image2.png)
平均而言，每个感染流感的人都会感染1.3个其他人。称为流感的“ R0”。如果R0小于1.0，则感染停止传播并终结。如果超过1.0，则会扩散。对于中国境外的新冠病毒，R0当前为2-3。这个范围听起来很小，但是在20个“世代”感染者继续感染后，R0为1.3将导致146例感染，而R0为2.5将导致3600万感染！（当然，这是非常粗略的，忽略了许多现实世界的影响，但这是合理的说明了新冠病毒与流感在所有其他条件相同的情况下的相对差异）。

注意，R0不是疾病的某些基本属性。它在很大程度上取决于响应，并且可以随时间变化2。最值得注意的是，在中国，针对新冠病毒的R0大幅下降，目前已接近1.0！你问怎么做到的？通过大规模实施在美国这样的国家难以想象措施，例如，完全封锁了许多大城市，并开发了一种测试程序，每周可以对一百万以上的人进行测试。

社交媒体（包括来自诸如埃隆·马斯克（Elon Musk）等有大量粉丝的帐户）上大量出现的一个问题是对数增长和指数增长之间差异的误解。对数增长是指实际中流行病传播的“S形”增长模式。显然，指数增长不可能永远持续下去，不然受感染的人数将超过世界上的人数！因此，最终感染率必然降低，导致随时间推移呈S形（称为Sigmoid）增长速度。但是，减少增长只是出于某种原因而不是魔法。主要原因是：

- 大规模的有效的社会响应，或
- 大多数人被感染，以致可被感染的健康人减少

因此，将对数增长模式作为“控制”大流行的一种方式是没有道理的。

很难直观地了解新冠病毒对社会的影响的另一件事是，感染和住院之间存在非常显著的延迟——通常在11天左右。这段时间似乎并不长，但是将其与那段时间的感染人数进行比较，则意味着当你注意到医院的病床已满时，总感染人数已经比就诊人数的增加了5-10倍。

请注意，有一些早期迹象表明，对您所在地区的影响至少在某种程度上取决于气候。论文[Temperature and latitude analysis to predict potential spread and seasonality for COVID-19](https://poseidon01.ssrn.com/delivery.php?ID=091071099092098096101097074089104068104013035023062021010031112088025099126064001093097030102106046016114116082016095089113023126034089078012119081090111118122007110026000085123071022022127025026080005029001020025126022000066075021086079031101116126112&EXT=pdf)指出，该疾病迄今已在温和的气候中传播（对我们而言，不幸的是，我们居住的旧金山的温度范围恰在该范围内；它还涵盖了欧洲的主要人口中心，包括伦敦。

## “不要惊慌，保持冷静。”毫无用处
我们在社交媒体上看到的一种普遍的回应是，人们指出了引起关注的原因，即“不要惊慌”或“保持冷静”。至少可以说，这没有帮助。没有人暗示恐慌是一种适当的应对措施。但是，出于某些原因，“保持冷静”在某些圈子中是一种非常普遍的反应（但在任何流行病学家中，其工作就是追踪这些事情）。也许“保持镇定”可以使某些人对自己的无所作为感到更好，或者使他们觉得比他们想象中的无头鸡跑来跑去的人优越。

但是“保持冷静”很容易导致准备和响应失败。在中国，数以千万计的人被封锁，并在达到美国目前的统计数字时建造了两家新医院。意大利等待时间太长，仅在今天（3月8日星期日），他们就报告了1492例新病例和133例新死亡，尽管锁定了1600万人。根据我们目前可以确定的最佳信息，就感染统计数据而言，仅在2-3周前，意大利与美国和英国在今天的位置相同。

请注意，在此阶段，几乎所有关于新冠病毒的事情都悬而未决。我们真的不知道它的感染速度或死亡率，我们不知道它在表面上保持活跃的时间，我们也不知道它是否可以在温暖的条件下生存和传播。我们拥有的一切都是基于人们能够汇总的最佳信息的最新最佳猜测。请记住，这些信息的绝大部分都在中国。目前，了解迄今为止中国现状的最好方法是阅读[Report of the WHO-China Joint Mission on Coronavirus Disease 2019](https://www.who.int/docs/default-source/coronaviruse/who-china-joint-mission-on-covid-19-final-report.pdf)由中国，德国，日本，韩国，尼日利亚，俄罗斯，新加坡，美国和世界卫生组织（WHO）的联合任务得来。

当存在不确定性时，也许这将不会是全球性的大流行，并且可能在没有医院系统崩溃的情况下一切都过去了，这并不意味着正确的应对措施是不采取任何行动。在任何威胁建模情况下，这都是极大的推测，而不是最佳的响应。像意大利和中国这样的国家也无缘无故地有效关闭其大部分经济体，这似乎也极不可能。这也与我们在受感染地区实地看到的实际影响不一致，因为那里的医疗系统无法应对（例如，意大利正在使用462顶帐篷进行“预分诊”，并且仍然需要[从受感染的地区转移ICU患者](https://www.repubblica.it/cronaca/2020/03/08/news/coronavirus_situazione_italia-250665818/?ref=RHPPTP-BH-I250661466-C12-P5-S1.12-T1)）。

相反，周到，合理的应对措施是遵循专家建议的步骤，以避免传播感染：

- 避免大群人群
- 取消活动
- 尽可能在家工作
- 出门在外时要洗手，出门时要经常洗手
- 避免触摸您的脸，尤其是在您出门在外时（不容易！）
- 消毒表面和包装（病毒可能会在表面上保持活跃9天，尽管至今仍无法确定）。

## 不只是关于你

如果您未满50岁，并且没有诸如免疫系统受损，心血管疾病，既往吸烟史或其他慢性病之类的风险因素，那么您可以放心新冠病毒不太可能杀死您。但是您的反应方式仍然非常重要。您仍然有被感染的机会，如果被感染，也有被他人感染的机会。平均而言，每个感染者再感染两个以上的人，并且在感染之前

他们表现出症状。如果您有自己关心的父母或祖父母，并计划与他们共度时光，后来发现您有责任以新冠病毒感染他们，那将是一个沉重的负担。

即使您未与50岁以上的人接触，也可能有更多的同事和熟人认识慢性病。[研究](https://www.talentinnovation.org/_private/assets/DisabilitiesInclusion_KeyFindings-CTI.pdf)表明，有些人会因为[害怕歧视](https://medium.com/@racheltho/the-tech-industry-is-failing-people-with-disabilities-and-chronic-illnesses-8e8aa17937f3)而在工作场所隐瞒自己的健康状况。我们俩都属于高风险类别，但我们经常与之互动的许多人可能不知道这一点。

当然，这不仅与您周围的人有关。这是一个非常重要的道德问题。每个竭尽全力为控制病毒传播做出贡献的人都在帮助他们的整个社会减慢感染速度。正如Zeynep Tufekci[在《科学美国人》中写道](https://blogs.scientificamerican.com/observations/preparing-for-coronavirus-to-strike-the-u-s/)：“为这种病毒几乎不可避免的全球传播做准备……是您可以做的最亲社会，无私的事情之一”。她继续说：

> 我们应该做好准备，而不是因为我们可能会感到个人处于危险之中，而是为了帮助我们降低所有人的风险。我们不应该做准备，不是因为我们面临无法控制的世界末日场景，而是因为我们可以改变社会所面临的这一风险的方方面面。没错，您应该做好准备，因为您的邻居需要您进行准备，尤其是您的年长邻居，在医院工作的邻居，患有慢性疾病的邻居以及由于缺乏精神而没有准备或时间准备的邻居资源或时间。

这对我们个人造成了影响。我们在fast.ai创建的最大，最重要的课程代表了我们多年的工作成果，计划于一周内在旧金山大学开始。上周三（3月4日），我们决定将整个产品向[线上](https://twitter.com/jeremyphoward/status/1236088745251581952)转移。我们是最早进入在线课程的大型课程之一。我们为什么这样做？因为我们上周初意识到，如果我们进行此课程，我们就隐含地鼓励数百人在一个封闭的空间中聚会，这需要持续数周时间。将小组聚集在封闭的空间中是一件最糟糕的事情。在道德上，我们有责任确保至少在这种情况下不会发生这种情况。这是一个令人心碎的决定。我们与学生直接合作所花费的时间一直是每年最大的乐趣和最丰盛的时期之一。我们有计划从世界各地飞来的学生，我们真的不想让他们失望。

但我们知道这是正确的做法，因为否则我们可能会增加疾病在我们社会中的传播。

## 我们需要压平曲线
这是非常重要的，因为如果我们可以减慢社会中的感染速度，那么我们将为该社会中的医院提供时间来处理被感染的患者以及需要处理的常规患者负担。这被描述为“使曲线变平”，并且在此说明图中清楚显示：

[停留在虚线下意味着一切](https://www.fast.ai/images/coronavirus/image3.jpeg)

前国家卫生IT协调员Farzad Mostashari解释说：“每天都在发现新的病例，这些病例没有旅行史，也没有与已知病例的联系，我们知道，这些只是冰山一角，因为测试延迟。这意味着在接下来的两周内，被诊断出的病例数量将爆炸……在社会呈指数蔓延的情况下尝试进行收容，就像专注于在房屋着火时扑灭火花一样。发生这种情况时，我们需要将策略转变为缓解措施，采取保护措施以减缓传播并减少对医疗保健的峰值影响。”如果我们能够将疾病的传播控制在足够低的水平，以使我们的医院可以负担得起，那么人们就可以接受治疗。但是，如果案件来得太快，那么那些需要住院的人就无法得到。

根据[Liz Specht的说法](https://twitter.com/LizSpecht/status/1236095186737852416)，数字可能是这样的：

> 美国每1000人拥有约2.8张病床。人口3.3亿，这是大约100万张床。在任何给定时间，这些床中的65％已被占用。这样一来，全国约有33万张病床（在每年的流感季节等时候，这个时候可能会少一些）。让我们相信意大利的数字，并假设大约10％的病例足够严重，需要住院治疗。（请记住，对于许多患者而言，住院治疗要持续数周，换句话说，当床位上堆满COVID19患者时，周转速度将非常缓慢）。据此估算，到5月8日左右，美国所有开放的医院病床将被装满。（当然，关于这些病床是否适合隔离具有高传染性病毒的患者，这没什么好说的。）如果我们对严重病例的比例错误两倍，这只能将任一方向的床饱和时间线更改6天。如果20％的病例需要住院，我们将在5月2日之前用完床。如果只有5％的病例需要住院，我们可以在5月14日之前完成治疗。2.5％使我们到达5月20日。当然，这是假设其他原因（非COVID19）对床的需求没有增加，这似乎是一个可疑的假设。随着医疗保健系统的负担越来越重，Rx短缺等，通常管理得当的患有慢性病的人可能会发现自己陷入了严重的医疗困境，需要重症监护和住院治疗。

## 社会的反应决定一切
正如我们已经讨论过的那样，这种数学方法还不是确定的。中国已经表明，采取极端措施可以降低利差。越南成功做出反应的另一个很好的例子是越南，除其他外，在全国范围内开展了一次广告宣传活动（包括一首流行的歌曲！），迅速动员了社会的反应并确保人们适当地调整了自己的行为。

这不仅是一种假设情况，还清楚地显示在1918年的流感大流行中。在美国，两个城市对这种大流行表现出截然不同的反应：费城进行了200,000人的巨型游行，以帮助为战争筹集资金。但是圣路易斯实施了精心设计的流程，以最大程度地减少社交接触，从而减少病毒传播并取消所有大型事件。根据《[美国国家科学院院刊](https://www.pnas.org/content/104/18/7582)》的记录，这是每个城市的死亡人数：

![对1918年流感大流行采取不同应对措施的影响](https://www.fast.ai/images/coronavirus/image4.jpeg)

费城的局势变得极为严峻，甚至到了[没有足够的葬礼棺材或太平间](https://www.history.com/news/spanish-flu-pandemic-dead)足以应付大量因流感而死的人的地步。

理查德·贝瑟（Richard Besser）在2009年H1N1大流行期间曾担任疾病控制与预防中心的代理主任，[他说](https://www.washingtonpost.com/opinions/as-coronavirus-spreads-the-bill-for-our-public-health-failures-is-due/2020/03/05/9da09ed6-5f10-11ea-b29b-9db42f7803a7_story.html?utm_campaign=wp_week_in_ideas&utm_medium=email&utm_source=newsletter&wpisrc=nl_ideas)：“在美国，暴露的风险和保护自己及家人的能力取决于收入，获得医疗保健以及移民身份等等。”他指出：

> 当老年人和残疾人的日常生活和支持系统受到干扰时，他们面临的风险尤其大。那些难以获得医疗服务的人，包括农村和土著社会，在需要时可能会面临艰巨的距离。正如我们在华盛顿州已经看到的那样，居住在近处的人们（无论是在公共住房，疗养院，监狱，庇护所，甚至是街头无家可归者中）可能会遭受海浪的折磨。低工资零工经济的脆弱性，无薪的工人和不稳定的工作时间表，将在这场危机中向所有人公开。询问每小时支付的60％的美国劳动力，在有需要的时候请假有多容易。

美国劳工统计局显示，在收入最低的阶层中，只有[不到三分之一](https://www.bls.gov/opub/ted/2018/higher-wage-workers-more-likely-than-lower-wage-workers-to-have-paid-leave-benefits-in-2018.htm)的人可以享受带薪病假：

![大多数可怜的美国人没有病假，所以必须去上班](https://www.fast.ai/images/coronavirus/image5.png)

## 在美国，信息不通畅
在美国，最大的问题之一是很少进行测试，并且测试结果没有正确共享，这意味着我们不知道实际发生了什么。先前的FDA专员Scott Gottlieb解释说，在西雅图进行了更好的测试，而且我们在那里看到了感染：“我们之所以很早就知道西雅图新冠病毒的爆发是因为独立科学家进行了前哨监视工作。在其他城市，这种监视从未完全进行。因此，其他美国热点可能尚未被完全检测到。”据《[大西洋报](https://www.theatlantic.com/health/archive/2020/03/how-many-americans-have-been-tested-coronavirus/607597/)》报道，副总统迈克·彭斯（Mike Pence）承诺本周将进行“大约150万次测试”，但目前在美国各地只有不到2,000人接受了测试。来自[COVID跟踪项目](https://docs.google.com/spreadsheets/u/1/d/e/2PACX-1vRwAqp96T9sYYq2-i7Tj0pvTf6XVHjDSMIKBdZHXiCGGdNC0ypEU9NbngS8mxea55JuCFuua1MUeOj5/pubhtml)，《大西洋报》的Robinson Meyer和Alexis Madrigal说：

> 我们收集的数据表明，美国人对新冠病毒及其引起的疾病新冠病毒的反应十分缓慢，特别是与其他发达国家相比。疾病预防控制中心八天前证实，该病毒正在美国社会传播-它正在感染既未出国旅行也未与其他人接触的美国人。在韩国，第一例社会传播病例在一周内接受了超过66,650人的测试，并且很快就可以每天测试10,000人。

问题的一部分在于，这已经成为一个政治问题。特别是，唐纳德·特朗普总统已明确表示，他希望看到“人数”（即美国的受感染人数）保持较低水平。这是个优化指标干扰在实践中取得好结果的例子。（有关此问题的更多信息，请参阅《数据科学伦理》论文《[度量标准的问题是人工智能的基本问题](https://arxiv.org/abs/2002.08512)》）。Google的AI负责人Jeff Dean[在推特上发布](https://twitter.com/JeffDean/status/1236489084870119427)了他对政治化虚假信息问题的关注：

> 在世卫组织工作时，我参加了全球艾滋病规划（现为艾滋病规划署），旨在帮助世界应对艾滋病毒/艾滋病的大流行。那里的员工都是敬业的医生和科学家，他们全神贯注于帮助解决这一危机。在危机时期，清晰，准确的信息对于帮助每个人（国家，州和地方政府，公司，非政府组织，学校，家庭和个人）做出正确而明智的决定至关重要。有了正确的信息和政策来聆听最好的医学和科学专家的意见，我们所有人都将面临诸如艾滋病毒/艾滋病或新冠病毒所面临的挑战。由于政治利益驱使虚假信息，存在面对现实的风险，那就是面对大流行病时不能迅速果断地采取行动，并积极鼓励实际上会更快传播疾病的行为，从而使事情变得更糟。整个情况难以观察。

在透明度方面，似乎没有改变的政治意愿。据《连线》报道，卫生和公共服务部长亚历克斯·阿扎尔（Alex Azar）开始谈论医护人员用来确定某人是否感染了新冠状病毒的测试。这些工具的缺乏意味着危险的缺乏有关该病在美国的传播和严重程度的流行病学信息，而政府方面的不透明加剧了这一情况。zar试图说，还有更多测试正在进行中，等待质量控制。”但是，他们继续说：

> 然后特朗普切断了阿扎尔：重要的是，我认为，无论现在还是昨天，任何需要测试的人都可以得到测试。他们在那里，他们有测试，测试很漂亮。任何需要测试的人都会得到测试，”特朗普说。这是不正确的。彭斯副总统星期四对记者说，美国没有足够的测试套件来满足需求。

其他国家的反应比美国快得多，而且反应明显得多。东南亚的许多国家/地区都显示出了不错的成绩，其中包括台湾，R0现在已降至0.3，以及新加坡，其被提议为[新冠病毒响应模型](https://www.medpagetoday.com/infectiousdisease/covid19/85254)。虽然不只是在亚洲，例如，在法国，禁止任何超过1000人的聚会，并且现在在三个地区关闭了学校。

## 结论
新冠病毒是一个重要的社会问题，我们可以而且应该都努力减少疾病的传播。这表示：

- 避免大批人群
- 取消活动
- 尽可能在家工作
- 出门在外时要洗手，出门时要洗手
- 避免触摸脸部，尤其是在出门在外时。

注意：由于急需解决这个问题，我们没有像平时一样谨慎地引用和赞扬我们所依赖的工作。如果我们错过了任何事情，请告诉我们。

感谢Sylvain Gugger和Alexis Gallagher的反馈和评论。

## 脚注

1. 流行病学家是研究疾病传播的人。事实证明，估计死亡率和R0之类的东西实际上是非常困难的，因此有一个专门研究此方面的领域。我们警告那些使用简单比率和统计数据来告诉您新冠病毒表现如何的人。相反，请看流行病学家所做的建模。

1. 好吧，从技术上讲并非如此。严格来说，“ R0”是指没有反应时的感染率。但这并不是我们真正关心的事情，因此让我们在这里对我们的定义有所草率。

1. 自从做出此决定以来，我们一直在努力寻找一种方法来运行虚拟课程，我们希望它将比面对面的版本更好。我们已经向全世界的所有人开放了它，并且将每天运行虚拟研究和项目组。

1. 我们还对生活方式进行了许多其他较小的更改，包括在家中锻炼而不是去健身房，将所有会议移至视频会议以及跳过我们期待已久的夜间活动。
