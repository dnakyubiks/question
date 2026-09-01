<!DOCTYPE html>
<html lang="ne">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>कक्षा १० हाजिरी जवाफ प्रतियोगिता (९० प्रश्नहरू)</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f6f9;
            color: #333;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
        }

        .scoreboard {
            position: sticky;
            top: 0;
            background: #1e3a8a;
            color: white;
            padding: 15px;
            border-radius: 8px;
            display: flex;
            justify-content: space-around;
            align-items: center;
            margin-bottom: 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .team-box {
            text-align: center;
            padding: 8px 16px;
            border-radius: 6px;
            background: rgba(255, 255, 255, 0.2);
        }

        .team-box.active {
            background: #d97706;
            font-weight: bold;
        }

        .score {
            font-size: 24px;
            font-weight: bold;
        }

        .turn-bar {
            background: #0d9488;
            color: white;
            text-align: center;
            padding: 10px;
            border-radius: 6px;
            font-size: 18px;
            margin-bottom: 20px;
            font-weight: bold;
        }

        .card {
            background: white;
            padding: 25px;
            border-radius: 8px;
            border: 1px solid #ccc;
        }

        .jump-container {
            margin-bottom: 15px;
            background: #e2e8f0;
            padding: 10px;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 10px;
            flex-wrap: wrap;
        }

        input[type="text"], input[type="number"], select {
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
        }

        button {
            background: #1e3a8a;
            color: white;
            border: none;
            padding: 10px 18px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }

        button:hover {
            opacity: 0.9;
        }

        .options-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin: 20px 0;
        }

        .opt-btn {
            background: #f1f5f9;
            color: #333;
            border: 1px solid #cbd5e1;
            padding: 12px;
            border-radius: 6px;
            text-align: left;
            font-size: 16px;
            cursor: pointer;
        }

        .controls {
            display: flex;
            justify-content: space-between;
        }

        .pass-btn {
            background: #64748b;
        }

        .home-btn {
            background: #b91c1c;
        }

        .hidden {
            display: none;
        }

        .form-group {
            margin-bottom: 15px;
        }
    </style>
</head>
<body>

<div class="container">

    <div id="scoreboard" class="scoreboard hidden">
        <div id="t1-box" class="team-box">
            <div id="t1-name">समूह १</div>
            <div id="t1-score" class="score">०</div>
        </div>
        <div>VS</div>
        <div id="t2-box" class="team-box">
            <div id="t2-name">समूह २</div>
            <div id="t2-score" class="score">०</div>
        </div>
    </div>

    <div id="turn-bar" class="turn-bar hidden">
        अहिले पालो: <span id="current-turn-name">-</span>
    </div>

    <div id="setup-screen" class="card">
        <h2>कक्षा १० हाजिरी जवाफ प्रतियोगिता</h2>
        <div class="form-group">
            <label>पहिलो समूहको नाम: </label><br>
            <input type="text" id="team1-input" placeholder="उदाहरण: सगरमाथा" style="width: 80%;">
        </div>
        <div class="form-group">
            <label>दोस्रो समूहको नाम: </label><br>
            <input type="text" id="team2-input" placeholder="उदाहरण: अन्नपूर्ण" style="width: 80%;">
        </div>
        <div class="form-group">
            <label>विषय छान्नुहोस् (Category): </label><br>
            <select id="category-select" style="width: 83%;">
                <option value="ALL">सबै मिसाएर (All Categories - 90 Questions)</option>
                <option value="मिश्रित">मिश्रित (Mixed: गाउँ खाने कथा, ट्रिकी, इतिहास - 30 Questions)</option>
                <option value="सामाजिक">सामाजिक शिक्षा (Social Studies - 30 Questions)</option>
                <option value="कम्प्युटर">कम्प्युटर (Computer Science - 30 Questions)</option>
            </select>
        </div>
        <button onclick="startQuiz()">सुरु गर्नुहोस्</button>
    </div>

    <div id="quiz-screen" class="card hidden">
        
        <div class="jump-container">
            <div>
                <label for="jump-num">प्रश्न नम्बरमा जानुहोस्: </label>
                <input type="number" id="jump-num" min="1" style="width: 80px;">
                <button onclick="jumpToQuestion()">जानुहोस्</button>
            </div>
            <button class="home-btn" onclick="goHome()">गृहपृष्ठ (Home)</button>
        </div>

        <b id="q-category" style="color: #0d9488;">[विषय]</b>
        <h3 id="q-number">प्रश्न १:</h3>
        <h2 id="q-text">प्रश्न?</h2>

        <div class="options-grid">
            <button class="opt-btn" onclick="checkAnswer(0)" id="o0"></button>
            <button class="opt-btn" onclick="checkAnswer(1)" id="o1"></button>
            <button class="opt-btn" onclick="checkAnswer(2)" id="o2"></button>
            <button class="opt-btn" onclick="checkAnswer(3)" id="o3"></button>
        </div>

        <div class="controls">
            <button class="pass-btn" onclick="passQuestion()">पास (Pass)</button>
            <button onclick="nextQuestion()">अर्को प्रश्न (Next)</button>
        </div>
    </div>

</div>

<script>
    const masterQuizData = [
        // ==========================================
        // १. मिश्रित (MIXED - 30 Questions)
        // ==========================================
        { cat: "मिश्रित", q: "कालो वर्ण, मुखमा ढोका, नबोलीकन गर्छ काम, के हो?", opts: ["कलम", "सिरक", "ताल्चा", "ऐना"], ans: 2 },
        { cat: "मिश्रित", q: "काठको घोडा, फलामको लगाम, घस्रिँदै जान्छ, के हो?", opts: ["गाडी", "हलो", "नाउ", "बन्चरो/बसिला"], ans: 3 },
        { cat: "मिश्रित", q: "समुद्रमा जन्मन्छ तर घरमा बस्छ, ओसिलो पाए बिलाउँछ, के हो?", opts: ["चिनी", "नुन", "बरफ", "पानी"], ans: 1 },
        { cat: "मिश्रित", q: "रातो बाछो, कालो गाई, बाछो दौडन्छ गाई उभिन्छ, के हो?", opts: ["आगो र धुवाँ", "घाम र छायाँ", "रात र दिन", "तारा र चन्द्रमा"], ans: 0 },
        { cat: "मिश्रित", q: "दुई भाइ ढोकामा उभिन्छन् तर एकआपसलाई कहिल्यै देख्दैनन्, के हो?", opts: ["कान", "हात", "आँखा", "गोडा"], ans: 2 },
        { cat: "मिश्रित", q: "झन् जति तास्यो झन् उती ठूलो देखिन्छ, के हो?", opts: ["रुख", "धागो", "कागज", "खाडल"], ans: 3 },
        { cat: "मिश्रित", q: "नाङ्लो भरि सुपारी, गन्नै नजान्ने व्यापारी, के हो?", opts: ["मकै", "आकाशका तारा", "स्याउ", "धान"], ans: 1 },
        { cat: "मिश्रित", q: "वरपर गुट्टी माँझमा घ्वाईं, के हो?", opts: ["दाँत र जिब्रो", "आँखा", "कान", "नाग"], ans: 0 },
        { cat: "मिश्रित", q: "भित्र सुन बाहिर चाँदी, के हो?", opts: ["केरा", "स्याउ", "अण्डा", "सुन्तला"], ans: 2 },
        { cat: "मिश्रित", q: "एक खुट्टे धामी थरथरी कामी, के हो?", opts: ["जुको", "रुख", "काँडा", "बन्चरो"], ans: 3 },
        
        { cat: "मिश्रित", q: "कुन यस्तो वस्तु हो जसलाई जति बढी सफा गर्यो, उति नै कालो हुँदै जान्छ?", opts: ["लुगा", "ब्ल्याकबोर्ड", "ऐना", "जुत्ता"], ans: 1 },
        { cat: "मिश्रित", q: "एउटा मानिस पानी परेको बेला छाता नओढी बाहिर हिँड्यो तर उसको एउटा पनि कपाल भिजेन, किन?", opts: ["उ तालुखुइले थियो", "उ टोपी लगाएको थियो", "पानी परेको थिएन", "उ रुखमुनि थियो"], ans: 0 },
        { cat: "मिश्रित", q: "तपाईं दौड प्रतियोगितामा दोस्रो स्थानको धावकलाई जित्नुभयो भने कुन स्थानमा पुग्नुहुन्छ?", opts: ["पहिलो", "तेस्रो", "दोस्रो", "चौथो"], ans: 2 },
        { cat: "मिश्रित", q: "नबोलीकन सबैभन्दा बढी ज्ञानका कुरा कसले सिकाउँछ?", opts: ["शिक्षक", "ऐना", "रेडियो", "किताब"], ans: 3 },
        { cat: "मिश्रित", q: "कुन चीज काट्दा मानिसहरू रुन्छन् तर कुनै दुःख भएको हुँदैन?", opts: ["प्याज", "कागज", "कपडा", "रुख"], ans: 0 },
        { cat: "मिश्रित", q: "आफ्नो शरीरको कुन अङ्ग कहिल्यै ठूलो हुँदैन, जन्मिँदा जत्रो छ त्यत्रै रहन्छ?", opts: ["कान", "आँखाको नानी", "नाक", "दाँत"], ans: 1 },
        { cat: "मिश्रित", q: "कुन यस्तो चीज हो जुन मानिसको आफ्नै हो तर अरूले बढी प्रयोग गर्छन्?", opts: ["पैसा", "घर", "नाम", "गाडी"], ans: 2 },
        { cat: "मिश्रित", q: "वर्षमा १ पटक, महिनामा २ पटक, हप्तामा ४ पटक र दिनमा ६ पटक आउने कुरा के हो?", opts: ["जोर नम्बर", "शनिबार", "बिदा", "अक्षर 'E'"], ans: 3 },

        { cat: "मिश्रित", q: "गोपाल वंशका प्रथम राजा को हुन्?", opts: ["वर सिंह", "भुक्तमान", "यक्ष गुप्त", "यलम्बर"], ans: 1 },
        { cat: "मिश्रित", q: "कोतपर्व कुन विक्रम संवत्‌मा घटेको ऐतिहासिक घटना हो?", opts: ["वि.सं. १९०१", "वि.सं. १९०७", "वि.सं. १९०३", "वि.सं. १९१४"], ans: 2 },
        { cat: "मिश्रित", q: "सुगौली सन्धिमा नेपालको तर्फबाट कसले हस्ताक्षर गरेका थिए?", opts: ["गजराज मिश्र", "भीमसेन थापा", "अमरसिंह थापा", "रणबहादुर शाह"], ans: 0 },
        { cat: "मिश्रित", q: "नेपालमा दासप्रथाको अन्त्य गर्ने राणा प्रधानमन्त्री को हुन्?", opts: ["जंगबहादुर", "देव शमशेर", "वीर शमशेर", "चन्द्र शमशेर"], ans: 3 },
        { cat: "मिश्रित", q: "प्रजापरिषद्‌को स्थापना कुन सालमा भएको थियो?", opts: ["वि.सं. १९९७", "वि.सं. १९९३", "वि.सं. २००७", "वि.सं. २००९"], ans: 1 },
        { cat: "मिश्रित", q: "मानदेवले चलाएको सिक्कालाई के भनिन्छ?", opts: ["गुणाङ्क", "पशुपति सिक्का", "मानाङ्क", "चाँदी सिक्का"], ans: 2 },
        { cat: "मिश्रित", q: "नेपालका प्रथम शहीद लखन थापालाई कुन सालमा फाँसी दिइएको थियो?", opts: ["वि.सं. १९३३", "वि.सं. १९३५", "वि.सं. १९४०", "वि.सं. १९५०"], ans: 0 },
        { cat: "मिश्रित", q: "काठमाडौंका अन्तिम मल्ल राजा को हुन्?", opts: ["तेजनरसिंह मल्ल", "रणजीत मल्ल", "जयप्रकाश मल्ल", "यक्ष मल्ल"], ans: 2 },
        { cat: "मिश्रित", q: "भण्डारखाल पर्व कुन राणा प्रधानमन्त्रीको समयमा भएको थियो?", opts: ["वीर शमशेर", "जंगबहादुर राणा", "देव शमशेर", "चन्द्र शमशेर"], ans: 1 },
        { cat: "मिश्रित", q: "किरात वंशका प्रथम राजा को थिए?", opts: ["गस्ती", "निमिष", "भूमि वर्मा", "यलम्बर"], ans: 3 },
        { cat: "मिश्रित", q: "शाह उपाधि धारण गर्ने पहिलो राजा को हुन्?", opts: ["द्रव्य शाह", "कुलमण्डन खान", "पृथ्वीनारायण शाह", "नरभूपाल शाह"], ans: 1 },
        { cat: "मिश्रित", q: "नालापानीको युद्धमा नेपाली फौजको नेतृत्व कसले गरेका थिए?", opts: ["बलभद्र कुँवर", "उजिरसिंह थापा", "भक्ति थापा", "अमरसिंह थापा"], ans: 0 },

        // ==========================================
        // २. सामाजिक शिक्षा (SOCIAL STUDIES - 30 Questions)
        // ==========================================
        { cat: "सामाजिक", q: "नेपालको संविधान २०७२ अनुसार नेपालमा कतिवटा मौलिक हकको व्यवस्था गरिएको छ?", opts: ["२१ वटा", "३१ वटा", "२५ वटा", "३५ वटा"], ans: 1 },
        { cat: "सामाजिक", q: "नेपालको वर्तमान संविधान कहिले जारी भएको हो?", opts: ["२०७२ भदौ २८", "२०७१ कात्तिक २५", "२०७२ असोज ३", "२०७३ वैशाख १"], ans: 2 },
        { cat: "सामाजिक", q: "दिगो विकास लक्ष्य (SDG) मा जम्मा कतिवटा लक्ष्यहरू निर्धारण गरिएका छन्?", opts: ["१५ वटा", "२० वटा", "१० वटा", "१७ वटा"], ans: 3 },
        { cat: "सामाजिक", q: "नेपालमा स्थानीय तहको जम्मा संख्या कति रहेको छ?", opts: ["७५३ वटा", "७५० वटा", "७७ वटा", "५०० वटा"], ans: 0 },
        { cat: "सामाजिक", q: "नेपालको प्रतिनिधिसभामा जम्मा कति जना सांसद रहने व्यवस्था छ?", opts: ["३३० जना", "२७५ जना", "११० जना", "१६५ जना"], ans: 1 },
        { cat: "सामाजिक", q: "नेपालको सबैभन्दा ठूलो ताल रारा ताल कुन जिल्लामा पर्दछ?", opts: ["डोल्पा", "कास्की", "मुगु", "रसुवा"], ans: 2 },
        { cat: "सामाजिक", q: "नेपालको सबैभन्दा सुक्खा ठाउँ कुन हो?", opts: ["मनाङ", "डोल्पा", "जुम्ला", "मुस्ताङ"], ans: 3 },
        { cat: "सामाजिक", q: "नेपालको कुल क्षेत्रफल कति वर्ग किलोमिटर छ?", opts: ["१,४७,१८१", "१,४७,५१६", "१,५१,१८१", "१,४५,१८१"], ans: 0 },
        { cat: "सामाजिक", q: "लुम्बिनी प्रदेशमा जम्मा कतिवटा जिल्लाहरू रहेका छन्?", opts: ["१० वटा", "१२ वटा", "११ वटा", "१३ वटा"], ans: 1 },
        { cat: "सामाजिक", q: "नेपालको सबैभन्दा होचो भूभाग केचनाकलन कुन जिल्लामा पर्छ?", opts: ["मोरङ", "सुनसरी", "झापा", "सिरहा"], ans: 2 },
        { cat: "सामाजिक", q: "सप्तकोशी नदीको सबैभन्दा ठूलो सहायक नदी कुन हो?", opts: ["तमोर", "सुनकोशी", "दूधकोशी", "अरुण"], ans: 3 },
        { cat: "सामाजिक", q: "सार्क (SAARC) को स्थापना कहिले भएको थियो?", opts: ["८ डिसेम्बर १९८५", "१५ अगस्ट १९४७", "२४ अक्टोबर १९५०", "१ जनवरी १९९०"], ans: 0 },
        { cat: "सामाजिक", q: "मानव अधिकार दिवस कहिले मनाइन्छ?", opts: ["अक्टोबर २४", "डिसेम्बर १०", "मार्च ८", "जुन ५"], ans: 1 },
        { cat: "सामाजिक", q: "नेपालमा राष्ट्रिय जनगणना कति-कति वर्षमा आयोजना हुन्छ?", opts: ["५-५ वर्षमा", "८-८ वर्षमा", "१०-१० वर्षमा", "१२-१२ वर्षमा"], ans: 2 },
        { cat: "सामाजिक", q: "नेपालको संविधानअनुसार नेपालको सार्वभौमसत्ता कसमा निहित छ?", opts: ["राष्ट्रपतिमा", "प्रधानमन्त्रीमा", "संसदमा", "नेपाली जनतामा"], ans: 3 },
        { cat: "सामाजिक", q: "नेपालमा 'कमैया मुक्ति' को घोषणा कहिले भएको थियो?", opts: ["वि.सं. २०५७ साउन २", "वि.सं. २०६०", "वि.सं. २०५०", "वि.सं. २०६३"], ans: 0 },
        { cat: "सामाजिक", q: "भूकम्पको तीव्रता नाप्ने यन्त्रलाई के भनिन्छ?", opts: ["ब्यारोमिटर", "सिस्मोग्राफ (Seismograph)", "थर्मोमिटर", "अमिटर"], ans: 1 },
        { cat: "सामाजिक", q: "सार्क (SAARC) को सचिवालय कहाँ रहेको छ?", opts: ["नयाँ दिल्ली, भारत", "कोलम्बो, श्रीलंका", "काठमाडौं, नेपाल", "ढाका, बंगलादेश"], ans: 2 },
        { cat: "सामाजिक", q: "संयुक्त राष्ट्रसंघ (UNO) को स्थापना कहिले भएको थियो?", opts: ["१५ अगस्ट १९४७", "१ जनवरी १९५०", "१० डिसेम्बर १९४८", "२४ अक्टोबर १९४५"], ans: 3 },
        { cat: "सामाजिक", q: "नेपालमा जिल्ला समन्वय समितिको संख्या कति रहेको छ?", opts: ["७७ वटा", "७५ वटा", "१४ वटा", "७ वटा"], ans: 0 },
        { cat: "सामाजिक", q: "उपभोक्ता अधिकारको अवधारणा पहिलोपटक कुन देशबाट सुरु भएको हो?", opts: ["बेलायत", "अमेरिका", "फ्रान्स", "जर्मनी"], ans: 1 },
        { cat: "सामाजिक", q: "नेपालको पहिलो राजमार्ग कुन हो?", opts: ["महेंद्र राजपथ", "पृथ्वी राजमार्ग", "त्रिभुवन राजपथ", "अरनिको राजमार्ग"], ans: 2 },
        { cat: "सामाजिक", q: "नेपालमा वातावरण दिवस कहिले मनाइन्छ?", opts: ["अप्रिल २२", "मार्च २२", "सेप्टेम्बर १६", "जुन ५"], ans: 3 },
        { cat: "सामाजिक", q: "नेपालको राष्ट्रिय योजना आयोगको अध्यक्ष को हुने व्यवस्था छ?", opts: ["प्रधानमन्त्री", "अर्थमन्त्री", "योजनामन्त्री", "राष्ट्रपति"], ans: 0 },
        { cat: "सामाजिक", q: "रेडक्रसको अन्तर्राष्ट्रिय समितिको मुख्यालय कहाँ छ?", opts: ["पेरिस", "जेनेभा", "वासिङ्टन डीसी", "रोम"], ans: 1 },
        { cat: "सामाजिक", q: "नेपालको सबैभन्दा लामो नदी कुन हो?", opts: ["कोशी नदी", "गण्डकी नदी", "कर्णाली नदी", "महाकाली नदी"], ans: 2 },
        { cat: "सामाजिक", q: "नेपालको पूर्व-पश्चिम औसत लम्बाइ कति रहेको छ?", opts: ["१९३ किलोमिटर", "५०० किलोमिटर", "१००० किलोमिटर", "८८५ किलोमिटर"], ans: 3 },
        { cat: "सामाजिक", q: "नेपालको उत्तर-दक्षिण औसत चौडाइ कति छ?", opts: ["१९३ किलोमिटर", "८८५ किलोमिटर", "१४५ किलोमिटर", "२५० किलोमिटर"], ans: 0 },
        { cat: "सामाजिक", q: "नागरिकका कर्तव्यहरू नेपालको संविधानको कुन धारामा उल्लेख छन्?", opts: ["धारा १६", "धारा ४८", "धारा ३०", "धारा ५६"], ans: 1 },
        { cat: "सामाजिक", q: "नेपालमा लैङ्गिक हिंसाविरुद्धको १६ दिने अभियान कहिले मनाइन्छ?", opts: ["मार्च १ देखि १५ सम्म", "जनवरी १ देखि १६ सम्म", "नोभेम्बर २५ देखि डिसेम्बर १० सम्म", "अक्टोबर १० देखि २५ सम्म"], ans: 2 },

        // ==========================================
        // ३. कम्प्युटर (COMPUTER SCIENCE - 30 Questions)
        // ==========================================
        { cat: "कम्प्युटर", q: "कम्प्युटरको दिमाग (Brain of Computer) भनेर कसलाई चिनिन्छ?", opts: ["RAM", "Hard Disk", "Monitor", "CPU"], ans: 3 },
        { cat: "कम्प्युटर", q: "RAM को पूर्ण रूप (Full Form) के हो?", opts: ["Random Access Memory", "Read Access Memory", "Rapid Access Memory", "Run Access Memory"], ans: 0 },
        { cat: "कम्प्युटर", q: "कम्प्युटरका पिता (Father of Computer) कसलाई भनिन्छ?", opts: ["Alan Turing", "Charles Babbage", "John von Neumann", "Bill Gates"], ans: 1 },
        { cat: "कम्प्युटर", q: "१ मेगाबाइट (1 MB) मा कति किलोबाइट (KB) हुन्छ?", opts: ["1000 KB", "512 KB", "1024 KB", "2048 KB"], ans: 2 },
        { cat: "कम्प्युटर", q: "HTTP को पूर्ण रूप के हो?", opts: ["High Transfer Text Protocol", "Hyper Transfer Text Program", "Hypertext Technology Protocol", "Hypertext Transfer Protocol"], ans: 3 },
        { cat: "कम्प्युटर", q: "तलका मध्ये कुन इनपुट उपकरण (Input Device) हो?", opts: ["Mouse", "Printer", "Monitor", "Speaker"], ans: 0 },
        { cat: "कम्प्युटर", q: "इन्टरनेटमा वेबसाइटहरूको ठेगानालाई के भनिन्छ?", opts: ["IP Address", "URL", "HTML", "DNS"], ans: 1 },
        { cat: "कम्प्युटर", q: "ROM कस्तो प्रकारको मेमोरी हो?", opts: ["Volatile", "Temporary", "Non-Volatile", "Virtual"], ans: 2 },
        { cat: "कम्प्युटर", q: "संसारको पहिलो प्रोग्रामर कसलाई मानिन्छ?", opts: ["Charles Babbage", "Grace Hopper", "Steve Jobs", "Lady Ada Lovelace"], ans: 3 },
        { cat: "कम्प्युटर", q: "MS Word मा फाइल सेभ गर्ने शर्टकट की (Shortcut Key) कुन हो?", opts: ["Ctrl + S", "Ctrl + C", "Ctrl + P", "Ctrl + V"], ans: 0 },
        { cat: "कम्प्युटर", q: "BINARY प्रणालीमा कुन-कुन दुईवटा अङ्क मात्र प्रयोग गरिन्छन्?", opts: ["1 र 2", "0 र 1", "0 र 9", "1 र 10"], ans: 1 },
        { cat: "कम्प्युटर", q: "GUI को पूर्ण रूप के हो?", opts: ["General User Interface", "Global User Interaction", "Graphical User Interface", "Guided User Interface"], ans: 2 },
        { cat: "कम्प्युटर", q: "इमेल (Email) को आविष्कार कसले गरेका हुन्?", opts: ["Tim Berners-Lee", "Mark Zuckerberg", "Larry Page", "Ray Tomlinson"], ans: 3 },
        { cat: "कम्प्युटर", q: "WWW (World Wide Web) का आविष्कारक को हुन्?", opts: ["Tim Berners-Lee", "Bill Gates", "Steve Wozniak", "Vint Cerf"], ans: 0 },
        { cat: "कम्प्युटर", q: "कम्प्युटर भाइरस (Virus) ले मुख्यतया के गर्छ?", opts: ["कम्प्युटर सफा गर्छ", "डाटा वा प्रोग्राम बिगार्छ", "इन्टरनेट तीव्र बनाउँछ", "मेमोरी बढाउँछ"], ans: 1 },
        { cat: "कम्प्युटर", q: "LAN को पूर्ण रूप के हो?", opts: ["Large Area Network", "Long Access Network", "Local Area Network", "Logical Area Network"], ans: 2 },
        { cat: "कम्प्युटर", q: "सफ्टवेयर (Software) मुख्यतया कति प्रकारका हुन्छन्?", opts: ["३ प्रकार", "४ प्रकार", "५ प्रकार", "२ प्रकार (System र Application)"], ans: 3 },
        { cat: "कम्प्युटर", q: "कम्प्युटरमा टेक्स्ट वा फाइल 'Cut' गर्न कुन शर्टकट की प्रयोग गरिन्छ?", opts: ["Ctrl + X", "Ctrl + C", "Ctrl + Z", "Ctrl + Y"], ans: 0 },
        { cat: "कम्प्युटर", q: "पहिलो पुस्ताको कम्प्युटरमा कुन मुख्य प्रविधि प्रयोग गरिएको थियो?", opts: ["Transistors", "Vacuum Tubes", "Integrated Circuits (IC)", "Microprocessor"], ans: 1 },
        { cat: "कम्प्युटर", q: "IP Address मा IP को पूर्ण रूप के हो?", opts: ["Internal Protocol", "Information Protocol", "Internet Protocol", "Interactive Program"], ans: 2 },
        { cat: "कम्प्युटर", q: "PDF को पूर्ण रूप के हो?", opts: ["Public Document File", "Print Document Format", "Personal Document File", "Portable Document Format"], ans: 3 },
        { cat: "कम्प्युटर", q: "नेटवर्कमा कम्प्युटरहरूलाई जोड्ने केन्द्रीय उपकरण कुन हो?", opts: ["Switch / Hub", "Cable", "Monitor", "UPS"], ans: 0 },
        { cat: "कम्प्युटर", q: "८ बिट (8 bits) बराबर कति हुन्छ?", opts: ["1 KB", "1 Byte", "1 Nibble", "1 MB"], ans: 1 },
        { cat: "कम्प्युटर", q: "Operating System कुन सफ्टवेयरअन्तर्गत पर्दछ?", opts: ["Application Software", "Utility Software", "System Software", "Antivirus Software"], ans: 2 },
        { cat: "कम्प्युटर", q: "संसारको पहिलो इलेक्ट्रोनिक डिजिटल कम्प्युटर कुन हो?", opts: ["UNIVAC", "ABC", "EDVAC", "ENIAC"], ans: 3 },
        { cat: "कम्प्युटर", q: "कम्प्युटरमा हटाइएका (Deleted) फाइलहरू अस्थायी रूपमा कहाँ बस्छन्?", opts: ["Recycle Bin", "Control Panel", "My Computer", "Task Manager"], ans: 0 },
        { cat: "कम्प्युटर", q: "WiFi को पूर्ण रूप के हो?", opts: ["Wired Fiber", "Wireless Fidelity", "Wireless Function", "Wired Fidelity"], ans: 1 },
        { cat: "कम्प्युटर", q: "वेबपेज (Webpage) निर्माण गर्न कुन भाषा प्रयोग गरिन्छ?", opts: ["C++", "SQL", "HTML", "JAVA"], ans: 2 },
        { cat: "कम्प्युटर", q: "नेपालमा पहिलोपटक जनगणनाका लागि ल्याइएको कम्प्युटर कुन हो?", opts: ["IBM 360", "Apple II", "ICL 2950", "IBM 1401"], ans: 3 },
        { cat: "कम्प्युटर", q: "DATABASE मा डाटा सुरक्षित राख्न र व्यवस्थापन गर्न प्रयोग गरिने सफ्टवेयरलाई के भनिन्छ?", opts: ["DBMS", "DOS", "BIOS", "RAM"], ans: 0 }
    ];

    let quizData = [];
    let team1 = "समूह १";
    let team2 = "समूह २";
    let score1 = 0;
    let score2 = 0;

    let currentIndex = 0;
    let currentTurn = 1;
    let answered = false;

    function startQuiz() {
        const t1 = document.getElementById("team1-input").value.trim();
        const t2 = document.getElementById("team2-input").value.trim();
        const selectedCat = document.getElementById("category-select").value;

        if (t1 !== "") team1 = t1;
        if (t2 !== "") team2 = t2;

        if (selectedCat === "ALL") {
            quizData = [...masterQuizData];
        } else {
            quizData = masterQuizData.filter(item => item.cat === selectedCat);
        }

        score1 = 0;
        score2 = 0;
        currentIndex = 0;
        currentTurn = 1;

        document.getElementById("t1-name").innerText = team1;
        document.getElementById("t2-name").innerText = team2;
        document.getElementById("t1-score").innerText = score1;
        document.getElementById("t2-score").innerText = score2;

        document.getElementById("jump-num").max = quizData.length;

        document.getElementById("setup-screen").classList.add("hidden");
        document.getElementById("scoreboard").classList.remove("hidden");
        document.getElementById("turn-bar").classList.remove("hidden");
        document.getElementById("quiz-screen").classList.remove("hidden");

        updateTurnUI();
        loadQuestion();
    }

    function updateTurnUI() {
        const turnName = currentTurn === 1 ? team1 : team2;
        document.getElementById("current-turn-name").innerText = turnName;

        if (currentTurn === 1) {
            document.getElementById("t1-box").classList.add("active");
            document.getElementById("t2-box").classList.remove("active");
        } else {
            document.getElementById("t2-box").classList.add("active");
            document.getElementById("t1-box").classList.remove("active");
        }
    }

    function loadQuestion() {
        answered = false;
        const data = quizData[currentIndex];
        
        document.getElementById("q-category").innerText = `विषय: ${data.cat}`;
        document.getElementById("q-number").innerText = `प्रश्न ${currentIndex + 1} / ${quizData.length}:`;
        document.getElementById("q-text").innerText = data.q;

        for (let i = 0; i < 4; i++) {
            const btn = document.getElementById(`o${i}`);
            btn.innerText = `${i + 1}. ${data.opts[i]}`;
            btn.disabled = false;
            btn.style.background = "#f1f5f9";
            btn.style.color = "#333";
        }
    }

    function checkAnswer(chosenIndex) {
        if (answered) return;
        answered = true;

        const data = quizData[currentIndex];
        
        for (let i = 0; i < 4; i++) {
            document.getElementById(`o${i}`).disabled = true;
        }

        if (chosenIndex === data.ans) {
            document.getElementById(`o${chosenIndex}`).style.background = "#16a34a";
            document.getElementById(`o${chosenIndex}`).style.color = "white";
            
            if (currentTurn === 1) {
                score1 += 1;
                document.getElementById("t1-score").innerText = score1;
            } else {
                score2 += 1;
                document.getElementById("t2-score").innerText = score2;
            }
        } else {
            document.getElementById(`o${chosenIndex}`).style.background = "#dc2626";
            document.getElementById(`o${chosenIndex}`).style.color = "white";
            
            document.getElementById(`o${data.ans}`).style.background = "#16a34a";
            document.getElementById(`o${data.ans}`).style.color = "white";
        }

        switchTurn();
    }

    function passQuestion() {
        switchTurn();
        alert(`प्रश्न पास भयो। अब पालो: ${currentTurn === 1 ? team1 : team2}`);
    }

    function switchTurn() {
        currentTurn = currentTurn === 1 ? 2 : 1;
        updateTurnUI();
    }

    function nextQuestion() {
        if (currentIndex < quizData.length - 1) {
            currentIndex++;
            loadQuestion();
        } else {
            alert(`सबै ${quizData.length} वटा प्रश्नहरू सकिएका छन्!`);
        }
    }

    function jumpToQuestion() {
        const val = parseInt(document.getElementById("jump-num").value);
        if (val >= 1 && val <= quizData.length) {
            currentIndex = val - 1;
            loadQuestion();
        } else {
            alert(`कृपया १ देखि ${quizData.length} सम्मको नम्बर राख्नुहोस्।`);
        }
    }

    function goHome() {
        const confirmGo = confirm("के तपाईं गृहपृष्ठमा फर्कन चाहनुहुन्छ? हालसम्मको अङ्क रिसेट हुनेछ।");
        if (confirmGo) {
            document.getElementById("quiz-screen").classList.add("hidden");
            document.getElementById("scoreboard").classList.add("hidden");
            document.getElementById("turn-bar").classList.add("hidden");
            document.getElementById("setup-screen").classList.remove("hidden");
        }
    }
</script>

</body>
</html>
