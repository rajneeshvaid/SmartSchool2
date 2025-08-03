SmartSchool - Student Management Menu Blueprint
परिचय
"Student Management" SmartSchool सॉफ्टवेयर का एक मुख्य मॉड्यूल है, जो छात्रों से संबंधित डेटा और कार्यों को प्रभावी ढंग से प्रबंधित करता है। यह hierarchical, expandable, और dynamic menu है, जिसमें 15 sub-menus शामिल हैं। इसे भारतीय स्कूलों की जरूरतों (RTE, UDISE+, NEP 2025) को पूरा करने के लिए डिज़ाइन किया गया है, जिसमें centralized data management और WhatsApp/DigiLocker integration जैसी सुविधाएँ शामिल हैं।
Menu Structure
Student Management [menu_student_management]
├── Student Profile [menu_student_profile]
├── Document Management [menu_document_management]
│   ├── Upload Documents [menu_upload_documents]
│   ├── Print/Share/Export Documents [menu_print_share_export_documents]
│   │   ├── ID Card Generation [menu_id_card]
│   │   ├── QR Code Generator [menu_qr_code_generator]
│   │   ├── Transfer Certificate Generation [menu_transfer_certificate]
│   │   ├── Fee Status [menu_student_fee_status]
├── Section & House Management [menu_section_house_management]
├── Asset & Entitlement Tracking [menu_asset_tracking]
│   ├── Uniform/Book/Tablet Distribution [menu_asset_distribution]
│   ├── Lost & Found Register [menu_lost_found]
├── Attendance Management [menu_student_attendance]
│   ├── Attendance Record [menu_attendance_record]
│   ├── Leave Application [menu_leave_application]
├── Fee Management [menu_fee_management]
├── Scholarship Management [menu_scholarship]
├── Performance Tracking [menu_performance_tracking]
├── Health Monitoring [menu_health_monitoring]
├── Behavior and Discipline Tracking [menu_behavior_tracking]
├── Letter/Notice Issue [menu_letter_notice_issue]
├── Student Communication Log [menu_student_communication_log]
├── Special Needs Management [menu_special_needs]
├── Alumni Management [menu_alumni]

Menu Descriptions
Student Management [menu_student_management]
छात्रों से संबंधित सभी डेटा और कार्यों (प्रोफाइल, दस्तावेज़, उपस्थिति, शुल्क, आदि) को प्रबंधित करने का केंद्रीकृत मॉड्यूल।
Student Profile [menu_student_profile]
छात्र की पूरी जानकारी, जैसे RTE/UDISE+ डेटा, कॉन्टैक्ट डिटेल्स, मेडिकल रिपोर्ट्स, और शैक्षिक रिकॉर्ड को प्रबंधित करता है।
Document Management [menu_document_management]
छात्रों के दस्तावेज़ों को प्रबंधित करने का केंद्रीकृत मॉड्यूल, जिसमें अपलोड और print/share/export कार्य शामिल हैं।

Upload Documents [menu_upload_documents]: फोटो, प्रमाणपत्र, और RTE-संबंधित दस्तावेज़ अपलोड करता है।
Print/Share/Export Documents [menu_print_share_export_documents]: TC, ID कार्ड, और शुल्क स्थिति जैसे दस्तावेज़ प्रिंट/एक्सपोर्ट/साझा करता है।
ID Card Generation [menu_id_card]: व्यक्तिगत छात्र ID कार्ड डिज़ाइन और प्रिंट करता है।
QR Code Generator [menu_qr_code_generator]: छात्र ID कार्ड के लिए encoded डेटा के साथ QR कोड जनरेट करता है।
Transfer Certificate Generation [menu_transfer_certificate]: ट्रांसफर सर्टिफिकेट जनरेट करता है।
Fee Status [menu_student_fee_status]: व्यक्तिगत छात्र की शुल्क स्थिति, देय तिथियाँ, और रसीद जनरेशन को ट्रैक करता है।



Section & House Management [menu_section_house_management]
छात्रों को क्लास सेक्शन और हाउस असाइन या संशोधित करता है।
Asset & Entitlement Tracking [menu_asset_tracking]
छात्रों को दी गई संपत्तियों (यूनिफॉर्म, किताबें, टैबलेट) और खोई/मिली वस्तुओं का प्रबंधन करता है।

Uniform/Book/Tablet Distribution [menu_asset_distribution]: यूनिफॉर्म, किताबें, और टैबलेट के वितरण को प्रबंधित करता है।
Lost & Found Register [menu_lost_found]: खोई/मिली वस्तुओं का रजिस्टर प्रबंधित करता है।

Attendance Management [menu_student_attendance]
दैनिक/मासिक उपस्थिति और अवकाश आवेदनों को प्रबंधित करता है।

Attendance Record [menu_attendance_record]: छात्र या क्लास की उपस्थिति रिकॉर्ड और ट्रैक करता है।
Leave Application [menu_leave_application]: अवकाश आवेदनों को प्रबंधित और स्वीकृत/अस्वीकृत करता है।

Fee Management [menu_fee_management]
शुल्क संरचना, भुगतान स्थिति, देय तिथियाँ, और रसीद जनरेशन को प्रबंधित करता है।
Scholarship Management [menu_scholarship]
छात्रवृत्ति प्रकार, राशि, और आवेदन स्थिति को प्रबंधित करता है।
Performance Tracking [menu_performance_tracking]
शैक्षिक और गैर-शैक्षिक प्रगति और प्रोग्रेस रिपोर्ट्स को ट्रैक करता है।
Health Monitoring [menu_health_monitoring]
मेडिकल हिस्ट्री, वैक्सीनेशन, और आपातकालीन कॉन्टैक्ट्स को प्रबंधित करता है।
Behavior and Discipline Tracking [menu_behavior_tracking]
छात्रों के व्यवहार और अनुशासनात्मक कार्रवाइयों को ट्रैक करता है।
Letter/Notice Issue [menu_letter_notice_issue]
छात्रों/पैरेंट्स के लिए पत्र और नोटिस (जैसे PTM, इवेंट्स) जारी करता है।
Student Communication Log [menu_student_communication_log]
छात्र/पैरेंट्स के साथ संचार (WhatsApp, ईमेल, PTM) का रिकॉर्ड रखता है।
Special Needs Management [menu_special_needs]
विशेष जरूरतों वाले छात्रों (CWSN) के लिए IEPs और सपोर्ट रिकॉर्ड प्रबंधित करता है।
Alumni Management [menu_alumni]
पूर्व छात्रों का डेटाबेस प्रबंधित करता है, जिसमें इवेंट्स और फंडरेजिंग शामिल हैं।
