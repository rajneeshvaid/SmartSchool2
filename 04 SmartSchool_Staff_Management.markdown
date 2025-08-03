# SmartSchool Staff Management Blueprint

## परिचय
"Staff Management" मेनू SmartSchool सॉफ्टवेयर का एक कोर मॉड्यूल है, जो स्कूल के स्टाफ (प्रशासनिक, शिक्षक, और गैर-शिक्षक) से संबंधित डेटा और कार्यों को प्रभावी ढंग से प्रबंधित करता है। यह मेनू हायरार्किकल, एक्सपैंडेबल, और डायनामिक है, जिसमें 5 मुख्य मेनू और उनके सब-मेनू व सब-सब-मेनू शामिल हैं। यह मॉड्यूल भारतीय स्कूलों की जरूरतों (UDISE+, NEP 2025) को पूरा करने के लिए डिज़ाइन किया गया है, जिसमें केंद्रीकृत डेटा प्रबंधन और WhatsApp/DigiLocker इंटीग्रेशन जैसी सुविधाएँ हैं।

## मेनू की विशेषताएँ
- **एक्सपैंड/कॉलैप्स**: कैटेगरीज़ और सब-मेनू को खोलने/बंद करने की सुविधा।
- **रोल-बेस्ड फ़िल्टरिंग**: यूजर रोल (Admin, HR Manager, Principal, Clerk) के आधार पर मेनू दृश्यता।
- **यूनिक ID**: Lowercase, underscores (जैसे `menu_staff_setup`), डायनामिक परमिशन्स और स्केलेबिलिटी के लिए।
- **ऑफलाइन सपोर्ट**: SQLite-आधारित लोकल स्टोरेज, ग्रामीण स्कूलों के लिए।
- **मल्टी-लैंग्वेज**: हिंदी, अंग्रेजी, और क्षेत्रीय भाषाओं में `gettext` सपोर्ट।
- **WhatsApp/DigiLocker इंटीग्रेशन**: नोटिफिकेशन, दस्तावेज़ शेयरिंग, और रसीद जनरेशन।
- **UDISE+/NEP अनुपालन**: APAR ID और डेटा मैपिंग।
- **डेटाबेस एकीकरण**: स्टाफ डेटा (`staff` टेबल) में सभी जानकारी केंद्रीकृत रूप से स्टोर की जाती है।

## मेनू स्ट्रक्चर
```
SmartSchool
└── Staff Management [menu_staff_management]
    ├── Staff Setup [menu_staff_setup]
    │   ├── Define Staff Types [menu_define_staff_types]
    │   ├── Define Designations [menu_define_designations]
    │   └── Define Employment Categories [menu_define_employment_categories]
    ├── Recruitment [menu_recruitment]
    │   ├── Administrators [menu_administrators]
    │   │   ├── Add New Applicant [menu_add_new_applicant]
    │   │   ├── Document Upload & Verification [menu_document_upload_verification]
    │   │   ├── Generate Proposal Letter [menu_generate_proposal_letter]
    │   │   ├── Accept & Add to Staff [menu_accept_add_to_staff]
    │   │   └── Generate Appointment Letter [menu_generate_appointment_letter]
    │   ├── Teachers [menu_teachers]
    │   │   ├── Add New Applicant [menu_add_new_applicant]
    │   │   ├── Document Upload & Verification [menu_document_upload_verification]
    │   │   ├── Generate Offer Letter [menu_generate_offer_letter]
    │   │   ├── Accept & Add to Staff [menu_accept_add_to_staff]
    │   │   └── Generate Appointment Letter [menu_generate_appointment_letter]
    │   └── Non-Teaching Staff [menu_non_teaching_staff]
    │       ├── Add New Applicant [menu_add_new_applicant]
    │       ├── Document Upload & Verification [menu_document_upload_verification]
    │       ├── Generate Offer Letter [menu_generate_offer_letter]
    │       ├── Accept & Add to Staff [menu_accept_add_to_staff]
    │       └── Generate Appointment Letter [menu_generate_appointment_letter]
    ├── Administrators [menu_administrators]
    │   ├── Administrator Profile [menu_administrator_profile]
    │   │   ├── View/Edit Profile [menu_view_edit_profile]
    │   │   ├── Documents Management [menu_documents_management]
    │   │   │   ├── Upload Documents [menu_upload_documents]
    │   │   │   └── Print/Share/Export Documents [menu_print_share_export_documents]
    │   │   ├── Confidential Notes [menu_confidential_notes]
    │   │   ├── QR Code Generation [menu_qr_code_generation]
    │   │   ├── ID Card Generation [menu_id_card_generation]
    │   │   └── Salary Tab [menu_salary_tab]
    │   └── Attendance & Leave Management [menu_attendance_leave_management]
    │       ├── Leave Quota [menu_leave_quota]
    │       ├── Attendance Record [menu_attendance_record]
    │       ├── Leave Record [menu_leave_record]
    │       └── Leave Application & Approval [menu_leave_application_approval]
    ├── Teachers Management [menu_teachers_management]
    │   ├── Teacher Profile [menu_teacher_profile]
    │   │   ├── View/Edit Profile [menu_view_edit_profile]
    │   │   ├── Documents Management [menu_documents_management]
    │   │   │   ├── Upload Documents [menu_upload_documents]
    │   │   │   └── Print/Share/Export Documents [menu_print_share_export_documents]
    │   │   ├── Confidential Notes [menu_confidential_notes]
    │   │   ├── QR Code Generation [menu_qr_code_generation]
    │   │   ├── ID Card Generation [menu_id_card_generation]
    │   │   └── Salary Tab [menu_salary_tab]
    │   └── Attendance & Leave Management [menu_attendance_leave_management]
    │       ├── Leave Quota [menu_leave_quota]
    │       ├── Attendance Record [menu_attendance_record]
    │       ├── Leave Record [menu_leave_record]
    │       └── Leave Application & Approval [menu_leave_application_approval]
    ├── Non-Teaching Staff Management [menu_non_teaching_staff_management]
    │   ├── Non-Teaching Staff Profile [menu_non_teaching_staff_profile]
    │   │   ├── View/Edit Profile [menu_view_edit_profile]
    │   │   ├── Documents Management [menu_documents_management]
    │   │   │   ├── Upload Documents [menu_upload_documents]
    │   │   │   └── Print/Share/Export Documents [menu_print_share_export_documents]
    │   │   ├── Confidential Notes [menu_confidential_notes]
    │   │   ├── QR Code Generation [menu_qr_code_generation]
    │   │   ├── ID Card Generation [menu_id_card_generation]
    │   │   └── Salary Tab [menu_salary_tab]
    │   └── Attendance & Leave Management [menu_attendance_leave_management]
    │       ├── Leave Quota [menu_leave_quota]
    │       ├── Attendance Record [menu_attendance_record]
    │       ├── Leave Record [menu_leave_record]
    │       └── Leave Application & Approval [menu_leave_application_approval]
    └── View Salary Information [menu_view_salary_information]
```

## विवरण और उपयोग

### Staff Management [menu_staff_management]
- **विवरण**: इस मेनू के द्वारा स्कूल के स्टाफ (प्रशासनिक, शिक्षक, और गैर-शिक्षक) से संबंधित सभी डेटा और कार्यों को प्रबंधित करने की सुविधा दी गई है। इसमें स्टाफ सेटअप, भर्ती, प्रोफाइल, उपस्थिति, और सैलरी जानकारी देखने की सुविधाएँ शामिल हैं।
- **उपयोग**:
  + स्टाफ डेटा का केंद्रीकृत प्रबंधन।
  + UDISE+ के लिए डेटा तैयार करना।
  + WhatsApp पर अपडेट्स भेजना।

### 1. Staff Setup [menu_staff_setup]
- **विवरण**: इस मेनू के द्वारा स्कूल के स्टाफ स्ट्रक्चर को शुरूआती रूप से तैयार करने की सुविधा दी गई है। इसका मकसद यह सुनिश्चित करना है कि SmartSchool में स्टाफ के विभिन्न प्रकार, पदनाम, और रोजगार श्रेणियाँ पहले से स्पष्ट हों, ताकि भर्ती, सैलरी, ड्यूटी असाइनमेंट, और अन्य प्रक्रियाएँ आसानी से चल सकें।
- **उपयोग**:
  + स्टाफ टाइप्स (जैसे Teaching, Administrative), डेजिग्नेशन (जैसे Principal, Teacher), और एम्प्लॉयमेंट कैटेगरीज़ (जैसे Permanent, Contractual) को परिभाषित करना।
  + UDISE+ के लिए स्टाफ डेटा तैयार करना।
  + WhatsApp पर सेटअप अपडेट्स भेजना।

#### 1.1 Define Staff Types [menu_define_staff_types]
- **विवरण**: इस मेनू के द्वारा स्टाफ के विभिन्न प्रकार और उनके ग्रेड्स को परिभाषित करने की सुविधा दी गई है। यहाँ स्टाफ टाइप (जैसे Teaching, Non-Teaching, Administrative) और ग्रेड (जैसे PGT, TGT, Clerk Grade I) तय किए जाते हैं, साथ ही हर ग्रेड के लिए बेसिक योग्यता और जॉब लेवल (जैसे Entry, Mid, Senior) भी जोड़ा जा सकता है।
- **उपयोग**:
  + स्टाफ प्रकारों को व्यवस्थित करना।
  + भर्ती के लिए आधार तैयार करना।
  + UDISE+ के लिए डेटा कैटेगरी बनाना।

#### 1.2 Define Designations [menu_define_designations]
- **विवरण**: इस मेनू के द्वारा स्टाफ के हर प्रकार और ग्रेड के तहत उपलब्ध पदनाम (जैसे Senior Biology Teacher, Office Assistant) को परिभाषित करने की सुविधा दी गई है। हर पद की जिम्मेदारियाँ, जरूरी योग्यता, और रिपोर्टिंग हायरार्की (किसके अधीन काम करना है) भी यहाँ तय की जा सकती है।
- **उपयोग**:
  + पदनामों को स्पष्ट करना।
  + स्टाफ की भूमिका निर्धारित करना।
  + UDISE+ के लिए पद डेटा तैयार करना।

#### 1.3 Define Employment Categories [menu_define_employment_categories]
- **विवरण**: इस मेनू के द्वारा स्टाफ के रोजगार श्रेणियाँ (जैसे Permanent, Contractual, Part-Time) और उनके विभाग (जैसे Science, Accounts) को परिभाषित करने की सुविधा दी गई है। यहाँ ड्यूटी शिफ्ट (जैसे Morning, Evening) भी तय की जा सकती है।
- **उपयोग**:
  + रोजगार प्रकार और शिफ्ट को व्यवस्थित करना।
  + ड्यूटी असाइनमेंट के लिए आधार तैयार करना।
  + UDISE+ डेटा में शामिल करना।

### 2. Recruitment [menu_recruitment]
- **विवरण**: इस मेनू के द्वारा स्कूल में नए स्टाफ की भर्ती प्रक्रिया को प्रबंधित करने की सुविधा दी गई है। इसमें आवेदन जमा करना, दस्तावेज़ सत्यापित करना, ऑफर/प्रपोजल पत्र जनरेट करना, ऑफर स्वीकार करना, और नियुक्ति पत्र जारी करना शामिल है।
- **उपयोग**:
  + विभिन्न स्टाफ प्रकारों (प्रशासनिक, शिक्षक, गैर-शिक्षक) के लिए भर्ती प्रक्रिया को डिजिटल और पारदर्शी बनाना।
  + UDISE+ के लिए स्टाफ डेटा अपलोड करना।
  + WhatsApp पर भर्ती स्टेटस नोटिफिकेशन भेजना।

#### 2.1 Administrators [menu_administrators]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ (जैसे प्रिंसिपल, HR) की भर्ती के लिए सुविधा दी गई है। यहाँ आवेदन प्रक्रिया से लेकर नियुक्ति तक के चरण हैं।
- **उपयोग**:
  + प्रशासनिक स्टाफ की भर्ती प्रबंधन।
  + दस्तावेज़ सत्यापन।
  + नियुक्ति पत्र जारी करना।

##### 2.1.1 Add New Applicant [menu_add_new_applicant]
- **विवरण**: इस मेनू के द्वारा नए प्रशासनिक स्टाफ के आवेदन को जोड़ने की सुविधा दी गई है, जिसमें नाम, APAR ID, योग्यता, और संपर्क जानकारी शामिल होती है।
- **उपयोग**:
  + आवेदकों का रिकॉर्ड बनाना।
  + भर्ती प्रक्रिया शुरू करना।

##### 2.1.2 Document Upload & Verification [menu_document_upload_verification]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के दस्तावेज़ (जैसे रिज्यूमे, सर्टिफिकेट) अपलोड और सत्यापन करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ों की जाँच।
  + सत्यापन स्टेटस अपडेट करना।

##### 2.1.3 Generate Proposal Letter [menu_generate_proposal_letter]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के लिए प्रपोजल पत्र जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ऑफर भेजने के लिए प्रपोजल पत्र तैयार करना।
  + WhatsApp पर साझा करना।

##### 2.1.4 Accept & Add to Staff [menu_accept_add_to_staff]
- **विवरण**: इस मेनू के द्वारा ऑफर स्वीकृति के बाद प्रशासनिक स्टाफ को डेटाबेस में जोड़ने की सुविधा दी गई है।
- **उपयोग**:
  + स्टाफ को आधिकारिक तौर पर शामिल करना।
  + रिकॉर्ड अपडेट करना।

##### 2.1.5 Generate Appointment Letter [menu_generate_appointment_letter]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के लिए नियुक्ति पत्र जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + नियुक्ति पत्र जारी करना।
  + DigiLocker पर अपलोड करना।

#### 2.2 Teachers [menu_teachers]
- **विवरण**: इस मेनू के द्वारा शिक्षकों की भर्ती के लिए सुविधा दी गई है, जिसमें आवेदन से नियुक्ति तक के चरण शामिल हैं।
- **उपयोग**:
  + शिक्षक भर्ती प्रक्रिया प्रबंधन।
  + UDISE+ डेटा अपलोड करना।

##### 2.2.1 Add New Applicant [menu_add_new_applicant]
- **विवरण**: इस मेनू के द्वारा नए शिक्षक के आवेदन को जोड़ने की सुविधा दी गई है।
- **उपयोग**:
  + शिक्षक आवेदकों का रिकॉर्ड बनाना।

##### 2.2.2 Document Upload & Verification [menu_document_upload_verification]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के दस्तावेज़ अपलोड और सत्यापन करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ जाँच।
  + सत्यापन स्टेटस अपडेट करना।

##### 2.2.3 Generate Offer Letter [menu_generate_offer_letter]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के लिए ऑफर पत्र जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ऑफर भेजने के लिए पत्र तैयार करना।
  + WhatsApp पर साझा करना।

##### 2.2.4 Accept & Add to Staff [menu_accept_add_to_staff]
- **विवरण**: इस मेनू के द्वारा ऑफर स्वीकृति के बाद शिक्षकों को स्टाफ में जोड़ने की सुविधा दी गई है।
- **उपयोग**:
  + शिक्षकों को आधिकारिक तौर पर शामिल करना।

##### 2.2.5 Generate Appointment Letter [menu_generate_appointment_letter]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के लिए नियुक्ति पत्र जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + नियुक्ति पत्र जारी करना।
  + DigiLocker पर अपलोड करना।

#### 2.3 Non-Teaching Staff [menu_non_teaching_staff]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ (जैसे क्लर्क, ड्राइवर) की भर्ती के लिए सुविधा दी गई है।
- **उपयोग**:
  + गैर-शिक्षक भर्ती प्रक्रिया प्रबंधन।
  + UDISE+ डेटा अपलोड करना।

##### 2.3.1 Add New Applicant [menu_add_new_applicant]
- **विवरण**: इस मेनू के द्वारा नए गैर-शिक्षक स्टाफ के आवेदन को जोड़ने की सुविधा दी गई है।
- **उपयोग**:
  + गैर-शिक्षक आवेदकों का रिकॉर्ड बनाना।

##### 2.3.2 Document Upload & Verification [menu_document_upload_verification]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के दस्तावेज़ अपलोड और सत्यापन करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ जाँच।
  + सत्यापन स्टेटस अपडेट करना।

##### 2.3.3 Generate Offer Letter [menu_generate_offer_letter]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के लिए ऑफर पत्र जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ऑफर भेजने के लिए पत्र तैयार करना।
  + WhatsApp पर साझा करना।

##### 2.3.4 Accept & Add to Staff [menu_accept_add_to_staff]
- **विवरण**: इस मेनू के द्वारा ऑफर स्वीकृति के बाद गैर-शिक्षक स्टाफ को शामिल करने की सुविधा दी गई है।
- **उपयोग**:
  + गैर-शिक्षक स्टाफ को आधिकारिक तौर पर जोड़ना।

##### 2.3.5 Generate Appointment Letter [menu_generate_appointment_letter]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के लिए नियुक्ति पत्र जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + नियुक्ति पत्र जारी करना।
  + DigiLocker पर अपलोड करना।

### 3. Administrators [menu_administrators]
- **विवरण**: इस मेनू के द्वारा स्कूल के प्रशासनिक स्टाफ (जैसे प्रिंसिपल, HR) से संबंधित सभी गतिविधियों को प्रबंधित करने की सुविधा दी गई है।
- **उपयोग**:
  + प्रशासनिक स्टाफ की जानकारी अपडेट करना।
  + दस्तावेज़ प्रबंधन।
  + सैलरी डेटा देखने के लिए Financial Management से लिंक करना।

#### 3.1 Administrator Profile [menu_administrator_profile]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ की प्रोफाइल और दस्तावेज़ प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + प्रोफाइल देखना/संपादित करना।
  + दस्तावेज़ अपलोड करना।
  + सैलरी टैब के माध्यम से जानकारी देखना।

##### 3.1.1 View/Edit Profile [menu_view_edit_profile]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ की जानकारी (नाम, APAR ID, योग्यता) देखने और संपादित करने की सुविधा दी गई है।
- **उपयोग**:
  + प्रोफाइल डेटा अपडेट करना।
  + UDISE+ के लिए डेटा तैयार करना।

##### 3.1.2 Documents Management [menu_documents_management]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के दस्तावेज़ों को प्रबंधित करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ अपलोड करना।
  + प्रिंट/साझा करना।

###### 3.1.2.1 Upload Documents [menu_upload_documents]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के दस्तावेज़ (रिज्यूमे, सर्टिफिकेट) अपलोड करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ जोड़ना।
  + WhatsApp पर साझा करना।

###### 3.1.2.2 Print/Share/Export Documents [menu_print_share_export_documents]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के दस्तावेज़ प्रिंट, साझा, या एक्सपोर्ट करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ PDF में एक्सपोर्ट करना।
  + DigiLocker पर अपलोड करना।

##### 3.1.3 Confidential Notes [menu_confidential_notes]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के गोपनीय नोट्स (जैसे प्रदर्शन) जोड़ने की सुविधा दी गई है।
- **उपयोग**:
  + गोपनीय टिप्पणियाँ रिकॉर्ड करना।
  + ऑडिट के लिए सुरक्षित रखना।

##### 3.1.4 QR Code Generation [menu_qr_code_generation]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के लिए QR कोड जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ID कार्ड पर QR कोड जोड़ना।
  + डेटा एक्सेस के लिए उपयोग करना।

##### 3.1.5 ID Card Generation [menu_id_card_generation]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के लिए ID कार्ड जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ID कार्ड प्रिंट करना।
  + WhatsApp पर साझा करना।

##### 3.1.6 Salary Tab [menu_salary_tab]
- **विवरण**: इस मेनू के द्वारा सैलरी जानकारी देखने के लिए Financial Management से लिंक करने की सुविधा दी गई है।
- **उपयोग**:
  + सैलरी डेटा देखना।
  + UDISE+ के लिए डेटा ट्रैक करना।

#### 3.2 Attendance & Leave Management [menu_attendance_leave_management]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ की उपस्थिति और छुट्टी प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + उपस्थिति रिकॉर्ड।
  + छुट्टी कोटा।
  + आवेदन प्रबंधन करना।

##### 3.2.1 Leave Quota [menu_leave_quota]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के लिए छुट्टी कोटा तय करने की सुविधा दी गई है।
- **उपयोग**:
  + छुट्टी की सीमा निर्धारित करना।
  + रिकॉर्ड रखना।

##### 3.2.2 Attendance Record [menu_attendance_record]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ की दैनिक/मासिक उपस्थिति रिकॉर्ड करने की सुविधा दी गई है।
- **उपयोग**:
  + उपस्थिति डेटा रिकॉर्ड करना।
  + UDISE+ के लिए अपलोड करना।

##### 3.2.3 Leave Record [menu_leave_record]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ की छुट्टी रिकॉर्ड देखने की सुविधा दी गई है।
- **उपयोग**:
  + छुट्टी का इतिहास ट्रैक करना।
  + रिपोर्ट तैयार करना।

##### 3.2.4 Leave Application & Approval [menu_leave_application_approval]
- **विवरण**: इस मेनू के द्वारा प्रशासनिक स्टाफ के छुट्टी आवेदन और अप्रूवल प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + आवेदन स्वीकृत/अस्वीकृत करना।
  + WhatsApp पर नोटिफिकेशन भेजना।

### 4. Teachers Management [menu_teachers_management]
- **विवरण**: इस मेनू के द्वारा स्कूल के शिक्षकों से संबंधित सभी गतिविधियों को प्रबंधित करने की सुविधा दी गई है।
- **उपयोग**:
  + शिक्षकों की जानकारी अपडेट करना।
  + दस्तावेज़ प्रबंधन।
  + सैलरी डेटा देखना।

#### 4.1 Teacher Profile [menu_teacher_profile]
- **विवरण**: इस मेनू के द्वारा शिक्षकों की प्रोफाइल और दस्तावेज़ प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + प्रोफाइल अपडेट करना।
  + दस्तावेज़ जोड़ना।
  + सैलरी टैब के माध्यम से जानकारी देखना।

##### 4.1.1 View/Edit Profile [menu_view_edit_profile]
- **विवरण**: इस मेनू के द्वारा शिक्षकों की जानकारी देखने और संपादित करने की सुविधा दी गई है।
- **उपयोग**:
  + प्रोफाइल डेटा अपडेट करना।
  + UDISE+ के लिए डेटा तैयार करना।

##### 4.1.2 Documents Management [menu_documents_management]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के दस्तावेज़ों को प्रबंधित करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ अपलोड करना।
  + प्रिंट/साझा करना।

###### 4.1.2.1 Upload Documents [menu_upload_documents]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के दस्तावेज़ अपलोड करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ जोड़ना।
  + WhatsApp पर साझा करना।

###### 4.1.2.2 Print/Share/Export Documents [menu_print_share_export_documents]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के दस्तावेज़ प्रिंट, साझा, या एक्सपोर्ट करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ PDF में एक्सपोर्ट करना।
  + DigiLocker पर अपलोड करना।

##### 4.1.3 Confidential Notes [menu_confidential_notes]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के गोपनीय नोट्स जोड़ने की सुविधा दी गई है।
- **उपयोग**:
  + गोपनीय टिप्पणियाँ रिकॉर्ड करना।
  + ऑडिट के लिए सुरक्षित रखना।

##### 4.1.4 QR Code Generation [menu_qr_code_generation]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के लिए QR कोड जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ID कार्ड पर QR कोड जोड़ना।
  + डेटा एक्सेस के लिए उपयोग करना।

##### 4.1.5 ID Card Generation [menu_id_card_generation]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के लिए ID कार्ड जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ID कार्ड प्रिंट करना।
  + WhatsApp पर साझा करना।

##### 4.1.6 Salary Tab [menu_salary_tab]
- **विवरण**: इस मेनू के द्वारा सैलरी जानकारी देखने के लिए Financial Management से लिंक करने की सुविधा दी गई है।
- **उपयोग**:
  + सैलरी डेटा देखना।
  + UDISE+ के लिए डेटा ट्रैक करना।

#### 4.2 Attendance & Leave Management [menu_attendance_leave_management]
- **विवरण**: इस मेनू के द्वारा शिक्षकों की उपस्थिति और छुट्टी प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + उपस्थिति रिकॉर्ड।
  + छुट्टी कोटा।
  + आवेदन प्रबंधन करना।

##### 4.2.1 Leave Quota [menu_leave_quota]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के लिए छुट्टी कोटा तय करने की सुविधा दी गई है।
- **उपयोग**:
  + छुट्टी की सीमा निर्धारित करना।
  + रिकॉर्ड रखना।

##### 4.2.2 Attendance Record [menu_attendance_record]
- **विवरण**: इस मेनू के द्वारा शिक्षकों की दैनिक/मासिक उपस्थिति रिकॉर्ड करने की सुविधा दी गई है।
- **उपयोग**:
  + उपस्थिति डेटा रिकॉर्ड करना।
  + UDISE+ के लिए अपलोड करना।

##### 4.2.3 Leave Record [menu_leave_record]
- **विवरण**: इस मेनू के द्वारा शिक्षकों की छुट्टी रिकॉर्ड देखने की सुविधा दी गई है।
- **उपयोग**:
  + छुट्टी का इतिहास ट्रैक करना।
  + रिपोर्ट तैयार करना।

##### 4.2.4 Leave Application & Approval [menu_leave_application_approval]
- **विवरण**: इस मेनू के द्वारा शिक्षकों के छुट्टी आवेदन और अप्रूवल प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + आवेदन स्वीकृत/अस्वीकृत करना।
  + WhatsApp पर नोटिफिकेशन भेजना।

### 5. Non-Teaching Staff Management [menu_non_teaching_staff_management]
- **विवरण**: इस मेनू के द्वारा स्कूल के गैर-शिक्षक स्टाफ (जैसे क्लर्क, ड्राइवर) से संबंधित सभी गतिविधियों को प्रबंधित करने की सुविधा दी गई है।
- **उपयोग**:
  + गैर-शिक्षक स्टाफ की जानकारी अपडेट करना।
  + दस्तावेज़ प्रबंधन।
  + सैलरी डेटा देखना।

#### 5.1 Non-Teaching Staff Profile [menu_non_teaching_staff_profile]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ की प्रोफाइल और दस्तावेज़ प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + प्रोफाइल अपडेट करना।
  + दस्तावेज़ जोड़ना।
  + सैलरी टैब के माध्यम से जानकारी देखना।

##### 5.1.1 View/Edit Profile [menu_view_edit_profile]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ की जानकारी देखने और संपादित करने की सुविधा दी गई है।
- **उपयोग**:
  + प्रोफाइल डेटा अपडेट करना।
  + UDISE+ के लिए डेटा तैयार करना।

##### 5.1.2 Documents Management [menu_documents_management]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के दस्तावेज़ों को प्रबंधित करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ अपलोड करना।
  + प्रिंट/साझा करना।

###### 5.1.2.1 Upload Documents [menu_upload_documents]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के दस्तावेज़ अपलोड करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ जोड़ना।
  + WhatsApp पर साझा करना।

###### 5.1.2.2 Print/Share/Export Documents [menu_print_share_export_documents]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के दस्तावेज़ प्रिंट, साझा, या एक्सपोर्ट करने की सुविधा दी गई है।
- **उपयोग**:
  + दस्तावेज़ PDF में एक्सपोर्ट करना।
  + DigiLocker पर अपलोड करना।

##### 5.1.3 Confidential Notes [menu_confidential_notes]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के गोपनीय नोट्स जोड़ने की सुविधा दी गई है।
- **उपयोग**:
  + गोपनीय टिप्पणियाँ रिकॉर्ड करना।
  + ऑडिट के लिए सुरक्षित रखना।

##### 5.1.4 QR Code Generation [menu_qr_code_generation]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के लिए QR कोड जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ID कार्ड पर QR कोड जोड़ना।
  + डेटा एक्सेस के लिए उपयोग करना।

##### 5.1.5 ID Card Generation [menu_id_card_generation]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के लिए ID कार्ड जनरेट करने की सुविधा दी गई है।
- **उपयोग**:
  + ID कार्ड प्रिंट करना।
  + WhatsApp पर साझा करना।

##### 5.1.6 Salary Tab [menu_salary_tab]
- **विवरण**: इस मेनू के द्वारा सैलरी जानकारी देखने के लिए Financial Management से लिंक करने की सुविधा दी गई है।
- **उपयोग**:
  + सैलरी डेटा देखना।
  + UDISE+ के लिए डेटा ट्रैक करना।

#### 5.2 Attendance & Leave Management [menu_attendance_leave_management]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ की उपस्थिति और छुट्टी प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + उपस्थिति रिकॉर्ड।
  + छुट्टी कोटा।
  + आवेदन प्रबंधन करना।

##### 5.2.1 Leave Quota [menu_leave_quota]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के लिए छुट्टी कोटा तय करने की सुविधा दी गई है।
- **उपयोग**:
  + छुट्टी की सीमा निर्धारित करना।
  + रिकॉर्ड रखना।

##### 5.2.2 Attendance Record [menu_attendance_record]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ की दैनिक/मासिक उपस्थिति रिकॉर्ड करने की सुविधा दी गई है।
- **उपयोग**:
  + उपस्थिति डेटा रिकॉर्ड करना।
  + UDISE+ के लिए अपलोड करना।

##### 5.2.3 Leave Record [menu_leave_record]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ की छुट्टी रिकॉर्ड देखने की सुविधा दी गई है।
- **उपयोग**:
  + छुट्टी का इतिहास ट्रैक करना।
  + रिपोर्ट तैयार करना।

##### 5.2.4 Leave Application & Approval [menu_leave_application_approval]
- **विवरण**: इस मेनू के द्वारा गैर-शिक्षक स्टाफ के छुट्टी आवेदन और अप्रूवल प्रबंधन करने की सुविधा दी गई है।
- **उपयोग**:
  + आवेदन स्वीकृत/अस्वीकृत करना।
  + WhatsApp पर नोटिफिकेशन भेजना।

### 6. View Salary Information [menu_view_salary_information]
- **विवरण**: इस मेनू के द्वारा स्टाफ की सैलरी जानकारी देखने की सुविधा दी गई है, जो Financial Management से डेटा लेता है।
- **उपयोग**:
  + Admin/Accountant सभी स्टाफ की सैलरी देख सकते हैं, जबकि अन्य स्टाफ सिर्फ अपनी सैलरी देख सकते हैं।
  + UDISE+ के लिए सैलरी डेटा ट्रैक करना।
  + WhatsApp पर सूचना भेजना।

## अतिरिक्त नोट्स
- **संरचना का आधार**: मेनू को यूजर-फ्रेंडली और मॉड्यूलर बनाया गया है, ताकि भविष्य में नए सब-मेनू जोड़े जा सकें।
- **UDISE+/NEP इंटीग्रेशन**: प्रत्येक सब-मेनू में UDISE+ डेटा फ़ील्ड्स (जैसे APAR ID) और NEP अनुपालन मैप किए गए हैं।
- **WhatsApp/DigiLocker इंटीग्रेशन**: अधिकांश सब-मेनू में WhatsApp नोटिफिकेशन/Sharing और DigiLocker अपलोड की सुविधा।