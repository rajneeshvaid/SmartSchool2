1 & 2
एडमिशन management 
Student मैनेजमेंट


SmartSchool Admission Management Blueprint
परिचय
Admission Management मेनू SmartSchool सॉफ्टवेयर का एक कोर मॉड्यूल है, जो स्कूल की प्रवेश प्रक्रिया को डिजिटल, पारदर्शी, और कार्यक्षम बनाता है। यह मॉड्यूल भारतीय स्कूलों की जरूरतों (RTE, UDISE+, NEP 2025) को ध्यान में रखकर डिज़ाइन किया गया है। यह हायरार्किकल, एक्सपैंडेबल, और डायनामिक है, जो प्रवेश के सभी चरणों—आवेदन जमा करने से लेकर अंतिम पुष्टि तक—को प्रबंधित करता है। प्रवेश प्रक्रिया के बाद, छात्र की विस्तृत जानकारी Student Management मॉड्यूल के माध्यम से अपडेट की जाएगी। मॉड्यूल में WhatsApp/DigiLocker इंटीग्रेशन, ऑफलाइन सपोर्ट, और रोल-बेस्ड एक्सेस शामिल हैं।
मेनू की विशेषताएँ
एक्सपैंड/कॉलैप्स: कैटेगरीज़ और सब-मेनू को खोलने/बंद करने की सुविधा।
रोल-बेस्ड फ़िल्टरिंग: यूजर रोल (Reception, Admission Clerk, Admission Officer, Accounts Dept., Principal/Academic Head) के आधार पर मेनू दृश्यता।
यूनिक ID: Lowercase, underscores (जैसे menu_submit_admission_form), डायनामिक परमिशन्स और स्केलेबिलिटी के लिए।
ऑफलाइन सपोर्ट: SQLite-आधारित लोकल स्टोरेज, ग्रामीण स्कूलों के लिए।
मल्टी-लैंग्वेज: हिंदी, अंग्रेजी, और क्षेत्रीय भाषाओं में gettext सपोर्ट।
WhatsApp/DigiLocker इंटीग्रेशन: नोटिफिकेशन, दस्तावेज़ शेयरिंग, और रसीद जनरेशन।
UDISE+/RTE अनुपालन: APAR ID, RTE मार्कर, और डेटा मैपिंग।
डेटाबेस एकीकरण: प्रवेश डेटा (admission_forms टेबल) से छात्र डेटा (students टेबल) में स्वचालित ट्रांसफर।
मेनू स्ट्रक्चर
SmartSchool
└── Admission Management [menu_admission_management]
    ├── Submit Admission Form [menu_submit_admission_form]
    ├── Document Verification [menu_document_verification]
    ├── Entrance Test / Interview [menu_entrance_test_interview]
    ├── Issue Fee Demand Letter [menu_fee_demand_letter]
    ├── Confirm Admission [menu_confirm_admission]
विवरण और उपयोग
Admission Management [menu_admission_management]
Screen Label: Admission Management
वास्तविक कार्य: यह केंद्रीकृत मॉड्यूल प्रवेश प्रक्रिया के सभी चरणों—आवेदन जमा करना, दस्तावेज़ सत्यापन, प्रवेश परीक्षा/इंटरव्यू, शुल्क मांग पत्र, और अंतिम पुष्टि—को प्रबंधित करता है। यह प्रक्रिया को डिजिटल और पारदर्शी बनाता है, जिससे स्कूल स्टाफ और पैरेंट्स के बीच संचार सुगम होता है।
उपयोग: 
RTE और non-RTE प्रवेश प्रक्रियाओं का प्रबंधन।
UDISE+ डेटा संग्रह और सिंकिंग (APAR ID, RTE मार्कर)।
पैरेंट्स के साथ WhatsApp/DigiLocker के माध्यम से त्वरित संचार।
ग्रामीण स्कूलों के लिए ऑफलाइन डेटा एंट्री और ऑटो-सिंकिंग।
स्कूल की प्रवेश प्रक्रिया को स्केलेबल और मॉड्यूलर बनाना।
1. Submit Admission Form [menu_submit_admission_form]
Screen Label: Submit Admission Form
वास्तविक कार्य: यह मॉड्यूल पैरेंट्स या छात्रों को ऑनलाइन/ऑफलाइन प्रवेश फॉर्म जमा करने की सुविधा देता है। फॉर्म में बेसिक जानकारी जैसे छात्र का नाम, जन्म तिथि, लिंग, अभिभावक जानकारी, और दस्तावेज़ अपलोड शामिल हैं। जमा होने पर स्टेटस "Pending Verification" पर सेट होता है।
उपयोग:
प्रवेश प्रक्रिया का पहला चरण, जो डिजिटल या मैनुअल फॉर्म स्वीकार करता है।
UDISE+ के लिए डेटा कैप्चर (जैसे APAR ID, RTE स्थिति)।
WhatsApp पर फॉर्म जमा होने की पुष्टि और स्टेटस अपडेट।
ऑफलाइन मोड में डेटा स्टोरेज और बाद में सिंकिंग।
रोल: Reception / Admission Clerk
फ़ील्ड्स:
छात्र जानकारी: नाम, जन्म तिथि, लिंग
अभिभावक जानकारी: नाम, मोबाइल, ईमेल, पता
शैक्षिक जानकारी: पिछला स्कूल, आवेदन की गई कक्षा
दस्तावेज़ अपलोड: फोटो, जन्म प्रमाणपत्र, आधार (वैकल्पिक), TC, RTE दस्तावेज़
डेटाबेस: डेटा admission_forms टेबल में स्टोर होता है।
आउटपुट: फॉर्म जमा होने पर "Form Submitted (Pending Verification)" स्टेटस, WhatsApp/ईमेल नोटिफिकेशन।
2. Document Verification [menu_document_verification]
Screen Label: Document Verification
वास्तविक कार्य: यह मॉड्यूल Admission Officer को जमा किए गए फॉर्म्स की सूची (स्टेटस: Pending Verification) दिखाता है, जहां वे अपलोड किए गए दस्तावेज़ (जन्म प्रमाणपत्र, TC, आधार, RTE दस्तावेज़) की जांच करते हैं। दस्तावेज़ को तीन स्टेटस में चिह्नित किया जा सकता है: Verified, Rejected, या Need Clarification।
उपयोग:
RTE अनुपालन के लिए दस्तावेज़ सत्यापन (जैसे आय प्रमाणपत्र)।
UDISE+ डेटा संग्रह के लिए सटीक जानकारी सुनिश्चित करना।
पैरेंट्स को WhatsApp पर सत्यापन स्टेटस अपडेट भेजना।
अस्वीकृत/क्लैरिफिकेशन केस में पैरेंट्स को कारण और अगले कदम की जानकारी।
रोल: Admission Officer
कार्य:
जमा किए गए फॉर्म्स की सूची देखना (Pending Verification)।
अपलोड किए गए दस्तावेज़ (PDF/इमेज) देखना और सत्यापित करना।
स्टेटस अपडेट: Verified ✅, Rejected ❌, Need Clarification 🟡।
डेटाबेस: admission_forms टेबल में स्टेटस अपडेट।
आउटपुट: सत्यापन स्टेटस WhatsApp/ईमेल पर पैरेंट्स को भेजा जाता है। Verified फॉर्म्स अगले चरण (Entrance Test/Interview) के लिए योग्य।
3. Entrance Test / Interview [menu_entrance_test_interview]
Screen Label: Entrance Test / Interview
वास्तविक कार्य: यह मॉड्यूल Verified छात्रों के लिए प्रवेश परीक्षा या इंटरव्यू शेड्यूल करता है, प्रदर्शन (मार्क्स/ग्रेड, टिप्पणियाँ) रिकॉर्ड करता है, और परिणाम को Selected, Rejected, या Waiting List के रूप में चिह्नित करता है।
उपयोग:
Non-RTE छात्रों के लिए मेरिट-आधारित चयन।
RTE छात्रों के लिए लॉटरी सिस्टम (यदि लागू हो)।
WhatsApp पर शेड्यूल और परिणाम भेजना।
UDISE+ के लिए प्रवेश डेटा (जैसे मेरिट लिस्ट) संग्रह।
रोल: Principal / Academic Head
फीचर्स:
Verified छात्रों के लिए टेस्ट/इंटरव्यू शेड्यूल करना (तारीख, समय, स्थान)।
प्रदर्शन रिकॉर्ड करना: मार्क्स/ग्रेड, टिप्पणियाँ।
परिणाम चिह्नित करना: Selected, Rejected, Waiting List।
डेटाबेस: admission_forms टेबल में टेस्ट/इंटरव्यू डेटा और परिणाम अपडेट।
आउटपुट: Selected छात्र अगले चरण (Issue Fee Demand Letter) के लिए योग्य। WhatsApp पर शेड्यूल और परिणाम।
4. Issue Fee Demand Letter [menu_fee_demand_letter]
Screen Label: Issue Fee Demand Letter
वास्तविक कार्य: Selected छात्रों के लिए सिस्टम स्वचालित रूप से कक्षा और शुल्क योजना के आधार पर मांग पत्र (Fee Demand Slip) जनरेट करता है। इसे प्रिंट, ईमेल, या WhatsApp पर भेजा जा सकता है। मांग पत्र में ड्यू डेट ट्रैक की जाती है।
उपयोग:
शुल्क संरचना में पारदर्शिता सुनिश्चित करना।
पैरेंट्स को WhatsApp/ईमेल पर मांग पत्र भेजना।
UDISE+ के लिए शुल्क डेटा संग्रह।
रोल: Accounts Dept.
कार्य:
Selected छात्रों के लिए शुल्क मांग पत्र जनरेट करना (ट्यूशन, परिवहन, अन्य)।
मांग पत्र प्रिंट/ईमेल/WhatsApp पर भेजना।
ड्यू डेट ट्रैक करना और रिमाइंडर भेजना।
डेटाबेस: admission_forms टेबल में शुल्क मांग स्टेटस अपडेट।
आउटपुट: स्टेटस "Fee Demanded"। WhatsApp पर मांग पत्र और रिमाइंडर।
5. Confirm Admission [menu_confirm_admission]
Screen Label: Confirm Admission
वास्तविक कार्य: शुल्क भुगतान की पुष्टि के बाद, छात्र को एक यूनिक Admission Number असाइन किया जाता है, और उनकी बेसिक जानकारी (admission_forms टेबल से) students टेबल में ट्रांसफर की जाती है। स्टेटस "Admitted" पर सेट होता है।
उपयोग:
प्रवेश प्रक्रिया को अंतिम रूप देना।
UDISE+ डेटा (APAR ID, छात्र प्रोफाइल) सिंकिंग।
WhatsApp/DigiLocker पर प्रवेश पत्र और पुष्टि भेजना।
Student Management मॉड्यूल के लिए डेटा तैयार करना।
रोल: Admission Clerk
कार्य:
शुल्क भुगतान की पुष्टि करना (✅ Yes)।
यूनिक Admission Number असाइन करना।
बेसिक जानकारी (admission_forms से) students टेबल में ट्रांसफर करना।
डेटाबेस: admission_forms से students टेबल में डेटा माइग्रेशन। स्टेटस "Admitted"।
आउटपुट: प्रवेश पत्र WhatsApp/DigiLocker पर। छात्र की विस्तृत जानकारी बाद में Student Management में अपडेट।
अतिरिक्त नोट्स
मॉड्यूलर डिज़ाइन: मेनू को स्केलेबल बनाया गया है, ताकि भविष्य में नए फीचर्स (जैसे AI-बेस्ड प्रवेश सुझाव, काउंसलिंग मॉड्यूल) जोड़े जा सकें।
UDISE+ और RTE इंटीग्रेशन: प्रत्येक सब-मेनू में UDISE+ फ़ील्ड्स (APAR ID, RTE मार्कर) और RTE अनुपालन (जैसे आय सत्यापन) मैप किए गए हैं।
WhatsApp/DigiLocker: सभी सब-मेनू में नोटिफिकेशन (फॉर्म स्टेटस, शुल्क रिमाइंडर, परिणाम) और दस्तावेज़ शेयरिंग (प्रवेश पत्र, मांग पत्र)।
ऑफलाइन सपोर्ट: SQLite-आधारित स्टोरेज ग्रामीण स्कूलों के लिए कम इंटरनेट वाले क्षेत्रों में कार्यक्षमता सुनिश्चित करता है।
रोल-बेस्ड एक्सेस: रोल्स (Reception, Admission Clerk, Admission Officer, Accounts Dept., Principal) के आधार पर विशिष्ट परमिशन्स, जैसे Clerk केवल फॉर्म जमा और पुष्टि देख सकता है।
डेटा फ्लो: प्रवेश प्रक्रिया का डेटा admission_forms टेबल से शुरू होता है और पुष्टि के बाद students टेबल में माइग्रेट होता है, जिससे Student Management मॉड्यूल के साथ निर्बाध एकीकरण होता है।


2
SmartSchool - "Student Management" मेनू ब्लूप्रिंट
परिचय
"Student Management" मेनू SmartSchool सॉफ्टवेयर का एक कोर मॉड्यूल है, जो छात्रों से संबंधित डेटा और कार्यों को प्रभावी ढंग से प्रबंधित करता है। यह मेनू हायरार्किकल, एक्सपैंडेबल, और डायनामिक है, जिसमें 14 सब-मेनू शामिल हैं। यह मॉड्यूल भारतीय स्कूलों की जरूरतों (RTE, UDISE+, NEP 2025) को पूरा करने के लिए डिज़ाइन किया गया है, जिसमें केंद्रीकृत डेटा प्रबंधन और WhatsApp/DigiLocker इंटीग्रेशन जैसी सुविधाएँ शामिल हैं। 



मेनू की विशेषताएँ
एक्सपैंड/कॉलैप्स: कैटेगरीज़ और सब-मेनू को खोलने/बंद करने की सुविधा। 
रोल-बेस्ड फ़िल्टरिंग: यूजर रोल (Admin, Teacher, Clerk) के आधार पर मेनू दृश्यता। 
यूनिक ID: Lowercase, underscores (जैसे menu_student_profile), डायनामिक परमिशन्स और स्केलेबिलिटी के लिए।



मेनू स्ट्रक्चर
Student Management [menu_student_management]├── Student Profile [menu_student_profile]├── Document Management [menu_document_management]│ ├── Upload Documents [menu_upload_documents]│ ├── Print/Share/Export Documents [menu_print_share_export_documents]│ │ ├── ID Card Generation [menu_id_card]│ │ ├── QR Code Generator [menu_qr_code_generator]│ │ ├── Transfer Certificate Generation [menu_transfer_certificate]│ │ ├── Fee Status [menu_student_fee_status]├── Section & House Management [menu_section_house_management]├── Asset & Entitlement Tracking [menu_asset_tracking]│ ├── Uniform/Book/Tablet Distribution [menu_asset_distribution]│ ├── Lost & Found Register [menu_lost_found]├── Attendance Management [menu_student_attendance]│ ├── Attendance Record [menu_attendance_record]│ ├── Leave Application [menu_leave_application]├── Fee Management [menu_fee_management]├── Scholarship Management [menu_scholarship]├── Performance Tracking [menu_performance_tracking]├── Health Monitoring [menu_health_monitoring]├── Behavior and Discipline Tracking [menu_behavior_tracking]├── Letter/Notice Issue [menu_letter_notice_issue]├── Student Communication Log [menu_student_communication_log]├── Special Needs Management [menu_special_needs] 



विवरण और उपयोग
Student Management [menu_student_management]
विवरण: छात्रों से संबंधित सभी डेटा और कार्यों (प्रोफाइल, दस्तावेज़, स्वास्थ्य, अनुशासन, उपस्थिति, शुल्क, संपत्ति, आदि) को प्रबंधित करने का केंद्रीकृत मॉड्यूल। 
उपयोग: छात्र प्रोफाइल्स, RTE/UDISE+ डेटा, और स्कूल की दैनिक जरूरतें।
Student Profile [menu_student_profile]
विवरण: एक केंद्रीकृत मॉड्यूल जो छात्र की समस्त जानकारी को एक स्थान पर देखने, जोड़ने, और अद्यतन करने की सुविधा देता है। इसमें नाम, रोल नंबर, क्लास, सेक्शन, हाउस, APAR ID, जन्म तिथि, पैरेंट्स का नाम, कॉन्टैक्ट, आधार (वैकल्पिक), और विशेष जरूरतें शामिल हैं। RTE और Sponsored Student से संबंधित जानकारी (जैसे RTE अनुपालन डेटा, प्रायोजक का नाम, फंड राशि, और दस्तावेज़) भी इसी सेक्शन में उपलब्ध और प्रबंधित की जा सकती हैं। 
छात्रों की जानकारी: एडमिशन फॉर्म के अतिरिक्त सभी जानकारी, जैसे विस्तृत कॉन्टैक्ट डिटेल्स (फोन, ईमेल, WhatsApp), मेडिकल रिपोर्ट्स (वैक्सीनेशन, ब्लड ग्रुप, स्वास्थ्य इतिहास), टेस्ट और टर्म परीक्षा परिणाम, शिक्षकों की टिप्पणियाँ, शिकायतें, और फीस भुगतान स्थिति, इस मॉड्यूल में प्रविष्ट और अद्यतन की जा सकती है। 
स्वचालित डेटा एकीकरण: अन्य मॉड्यूल्स से डेटा स्वतः एकीकृत होता है। 
उपयोग: RTE/UDISE+ अनुपालन, WhatsApp पर प्रोफाइल अपडेट्स, और केंद्रीकृत प्रोफाइल प्रबंधन। 
नोट: जानकारी अन्य मॉड्यूल्स में केवल व्यू-ओनली (read-only) मोड में उपलब्ध।
Document Management [menu_document_management]
विवरण: छात्रों से संबंधित सभी दस्तावेज़ों के प्रबंधन के लिए केंद्रीकृत मॉड्यूल, जिसमें अपलोड और प्रिंट/शेयर/एक्सपोर्ट कार्य शामिल हैं। 
उपयोग: RTE/UDISE+ के लिए आवश्यक दस्तावेज़ अपलोड, स्कूल द्वारा जनरेटेड दस्तावेज़ों को प्रिंट/एक्सपोर्ट, और WhatsApp/DigiLocker पर साझा करना।
Upload Documents [menu_upload_documents]
विवरण: फोटो, जन्म प्रमाणपत्र, आय/जाति/निवास प्रमाणपत्र, आधार, मेडिकल रिपोर्ट्स, आवेदन पत्र, और RTE/Sponsored Student दस्तावेज़ अपलोड और प्रबंधित करने की सुविधा। 
उपयोग: Student Profile से लिंक करना, कैटेगरीज़ में व्यवस्थित करना, WhatsApp पर स्कैन कॉपी साझा करना।
Print/Share/Export Documents [menu_print_share_export_documents]
विवरण: स्कूल द्वारा जनरेटेड दस्तावेज़, जैसे ट्रांसफर सर्टिफिकेट (TC), दाखिल-खारिज रिकॉर्ड, फीस स्टेटस, ID कार्ड, और प्रोग्रेस रिपोर्ट, को प्रिंट, PDF में एक्सपोर्ट, या WhatsApp/DigiLocker पर साझा करने की सुविधा। ID कार्ड प्रिंटिंग सामान्य रूप से अन्य संबंधित डिपार्टमेंट्स द्वारा बल्क में की जाएगी, लेकिन भविष्य में किसी एक छात्र के ID कार्ड में परिवर्तन के लिए इस मॉड्यूल का उपयोग किया जाएगा। 
उपयोग: डिजिटल सिग्नेचर के साथ दस्तावेज़ जनरेट करना, प्रोग्रेस रिपोर्ट/फीस रसीद साझा करना, और DigiLocker अपलोड।
ID Card Generation [menu_id_card]
विवरण: किसी एक छात्र के लिए स्कूल लोगो, फोटो, और डिटेल्स के साथ ID कार्ड डिज़ाइन और प्रिंट करना। ID कार्ड प्रिंटिंग सामान्य रूप से अन्य संबंधित डिपार्टमेंट्स द्वारा बल्क में की जाएगी, लेकिन भविष्य में किसी एक छात्र के ID कार्ड में परिवर्तन के लिए इस मॉड्यूल का उपयोग किया जाएगा। 
उपयोग: सुरक्षा, बायोमेट्रिक इंटीग्रेशन, और WhatsApp/DigiLocker पर शेयरिंग।
QR Code Generator [menu_qr_code_generator]
विवरण: किसी एक छात्र के ID कार्ड के लिए QR कोड जनरेट करने की सुविधा, जिसमें छात्र की जानकारी (जैसे APAR ID, नाम, क्लास) या अन्य डेटा (जैसे प्रोफाइल लिंक, उपस्थिति रिकॉर्ड) एन्कोड हो सकती है। 
उपयोग: 
ID कार्ड पर QR कोड जोड़ना, जो स्कैन करने पर Student Profile या अन्य जानकारी तक ले जाए। 
सुरक्षा और त्वरित डेटा एक्सेस (जैसे बायोमेट्रिक सत्यापन)। 
WhatsApp/DigiLocker पर QR कोड-आधारित ID शेयरिंग।
Transfer Certificate Generation [menu_transfer_certificate]
विवरण: किसी एक छात्र के लिए डिजिटल सिग्नेचर के साथ प्रोफेशनल TC जनरेट करना। 
उपयोग: DigiLocker अपलोड और WhatsApp शेयरिंग।
Fee Status [menu_student_fee_status]
विवरण: किसी एक छात्र के लिए शुल्क स्टेटस (पेड/पेंडिंग), ड्यू डेट्स, जुर्माना, और रसीद जनरेशन। 
उपयोग: WhatsApp पर शुल्क रिमाइंडर और UDISE+ के लिए फाइनेंशियल डेटा।
Section & House Management [menu_section_house_management]
विवरण: किसी एक छात्र को क्लास सेक्शन (जैसे Section A, B) और हाउस (जैसे Green House, Red House) असाइन करने, परिवर्तन करने, और पॉइंट्स, रैंकिंग, और कॉम्पिटिशन ट्रैकिंग की सुविधा। सेक्शन और हाउस असाइनमेंट सामान्य रूप से अन्य संबंधित डिपार्टमेंट्स द्वारा बल्क में किया जाएगा, लेकिन भविष्य में किसी एक छात्र के सेक्शन या हाउस में परिवर्तन के लिए इस मॉड्यूल का उपयोग किया जाएगा। 
उपयोग: 
किसी एक छात्र के लिए सेक्शन और हाउस असाइनमेंट का प्रबंधन और परिवर्तन। 
हाउस-आधारित प्रतियोगिताओं का आयोजन और पॉइंट्स ट्रैकिंग। 
WhatsApp पर रिजल्ट्स और अपडेट्स साझा करना। 
Student Profile में सेक्शन/हाउस डेटा एकीकरण।
Asset & Entitlement Tracking [menu_asset_tracking]
विवरण: छात्रों को दी जाने वाली संपत्तियों (जैसे यूनिफॉर्म, किताबें, टैबलेट) और खोई/मिली वस्तुओं के रिकॉर्ड का प्रबंधन। 
उपयोग: संपत्ति वितरण और खोई/मिली वस्तुओं का ट्रैकिंग, Student Profile में एकीकरण।
Uniform/Book/Tablet Distribution [menu_asset_distribution]
विवरण: छात्रों को यूनिफॉर्म, किताबें, टैबलेट, और अन्य शैक्षिक सामग्री के वितरण का प्रबंधन और रिकॉर्ड रखने की सुविधा। 
उपयोग: 
किसी एक छात्र या समूह के लिए संपत्ति वितरण रिकॉर्ड करना। 
WhatsApp पर वितरण की सूचना साझा करना। 
Student Profile में संपत्ति डेटा एकीकरण।
Lost & Found Register [menu_lost_found]
विवरण: खोई और मिली वस्तुओं (जैसे किताबें, यूनिफॉर्म, अन्य सामान) का रजिस्टर प्रबंधित करने की सुविधा। 
उपयोग: 
खोई/मिली वस्तुओं का रिकॉर्ड रखना और अपडेट करना। 
WhatsApp पर खोई/मिली वस्तुओं की सूचना साझा करना। 
Student Profile में एकीकरण।
Attendance Management [menu_student_attendance]
विवरण: दैनिक/मासिक उपस्थिति और अवकाश आवेदनों का प्रबंधन, जिसमें बायोमेट्रिक/मैनुअल एंट्री और लीव एप्लीकेशन शामिल हैं। 
उपयोग: UDISE+ डेटा, WhatsApp पर अनुपस्थिति अलर्ट, और अवकाश आवेदनों का प्रबंधन।
Attendance Record [menu_attendance_record]
विवरण: किसी एक छात्र या क्लास के लिए दैनिक/मासिक उपस्थिति को रिकॉर्ड करने और ट्रैक करने की सुविधा। 
उपयोग: 
बायोमेट्रिक या मैनुअल एंट्री के माध्यम से उपस्थिति रिकॉर्ड करना। 
UDISE+ के लिए उपस्थिति डेटा मैप करना। 
WhatsApp पर अनुपस्थिति अलर्ट भेजना। 
Student Profile में उपस्थिति डेटा एकीकरण।
Leave Application [menu_leave_application]
विवरण: छात्रों या पैरेंट्स द्वारा प्रस्तुत अवकाश आवेदनों को प्रबंधित करने, स्वीकृत/अस्वीकृत करने, और रिकॉर्ड रखने की सुविधा। 
उपयोग: 
अवकाश आवेदनों की समीक्षा और स्टेटस अपडेट। 
WhatsApp पर अवकाश स्वीकृति/अस्वीकृति नोटिफिकेशन। 
Student Profile और Attendance Record में एकीकरण।
Fee Management [menu_fee_management]
विवरण: छात्रों के शुल्क से संबंधित सभी कार्यों का प्रबंधन, जिसमें शुल्क संरचना (ट्यूशन, ट्रांसपोर्ट, आदि), भुगतान स्थिति (पेड/पेंडिंग), ड्यू डेट्स, जुर्माना, और रसीद जनरेशन शामिल हैं। सामान्य रूप से बल्क शुल्क प्रबंधन अन्य संबंधित डिपार्टमेंट्स द्वारा किया जाएगा, लेकिन भविष्य में किसी एक छात्र के शुल्क में परिवर्तन के लिए इस मॉड्यूल का उपयोग किया जाएगा। 
उपयोग: 
किसी एक छात्र के लिए शुल्क भुगतान का प्रबंधन और रसीद जनरेशन। 
WhatsApp पर शुल्क रिमाइंडर और रसीद साझा करना। 
UDISE+ के लिए फाइनेंशियल डेटा और Student Profile में एकीकरण।
Scholarship Management [menu_scholarship]
विवरण: छात्रवृत्ति प्रकार, राशि, आवेदन स्टेटस, और अप्रूवल का प्रबंधन। 
उपयोग: स्कॉलरशिप ट्रैकिंग, UDISE+/RTE डेटा, और WhatsApp नोटिफिकेशन।
Performance Tracking [menu_performance_tracking]
विवरण: शैक्षिक और गैर-शैक्षिक प्रोग्रेस, प्रोग्रेस रिपोर्ट्स। 
उपयोग: NEP 2025 लर्निंग आउटकम्स और WhatsApp अपडेट्स।
Health Monitoring [menu_health_monitoring]
विवरण: मेडिकल हिस्ट्री, वैक्सीनेशन, ब्लड ग्रुप, और आपातकालीन कॉन्टैक्ट्स। 
उपयोग: मेडिकल इमरजेंसी, UDISE+ हेल्थ डेटा, और Student Profile में एकीकरण।
Behavior and Discipline Tracking [menu_behavior_tracking]
विवरण: व्यवहार, अनुशासनात्मक कार्रवाइयाँ, और टिप्पणियाँ। 
उपयोग: NEP 2025 होलिस्टिक डेवलपमेंट और WhatsApp नोटिफिकेशन।
Letter/Notice Issue [menu_letter_notice_issue]
विवरण: छात्रों या पैरेंट्स के लिए पत्र (जैसे चेतावनी पत्र, सूचना पत्र) और नोटिस (जैसे PTM, इवेंट्स) जारी करने और प्रबंधित करने की सुविधा। 
उपयोग: 
व्यक्तिगत या समूह-आधारित पत्र/नोटिस जनरेट करना। 
WhatsApp/ईमेल पर पत्र/नोटिस साझा करना। 
Student Profile और Student Communication Log में एकीकरण।
Student Communication Log [menu_student_communication_log]
विवरण: छात्र/पैरेंट्स के साथ संचार का रिकॉर्ड (WhatsApp, ईमेल, PTM, पत्र/नोटिस)। 
उपयोग: संचार ट्रैकिंग और पारदर्शिता।
Special Needs Management [menu_special_needs]
विवरण: विशेष जरूरतों वाले छात्रों (CWSN) के लिए IEPs और सपोर्ट रिकॉर्ड। 
उपयोग: RTE/UDISE+ डेटा और व्यक्तिगत सपोर्ट प्लानिंग।



अतिरिक्त नोट्स
संरचना का आधार: मेनू को यूजर-फ्रेंडली और मॉड्यूलर बनाया गया है, ताकि भविष्य में नए सब-मेनू (जैसे AI-बेस्ड काउंसलिंग) जोड़े जा सकें। 
UDISE+ और RTE इंटीग्रेशन: प्रत्येक सब-मेनू में UDISE+ डेटा फ़ील्ड्स (जैसे APAR ID, CWSN) और RTE अनुपालन (जैसे स्कॉलरशिप, विशेष जरूरतें) मैप किए गए हैं। 
WhatsApp इंटीग्रेशन: अधिकांश सब-मेनू में WhatsApp नोटिफिकेशन/Shareing की सुविधा।
