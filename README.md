📁 Basic Git Snippets
Author: Sanjay Explorer

🔧 Git Configuration
Set Global Git User
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

Check Global Git Config
git config --global user.name
git config --global user.email

🌐 Remote Repository
Add Remote Origin
git remote add origin <repository_url>
# Example:
git remote add origin https://github.com/sanjayexplorer/basicgitsnippets

Clone Repository
git clone <repository_url>
# Example:
git clone https://github.com/sanjayexplorer/basicgitsnippets

📂 Git Basics
Check Hidden .git Folder
ls -a
git status

🔄 Git File Status Lifecycle
untracked -> modified -> staged -> committed -> unmodified
Untracked: New files not tracked by Git

Modified: Tracked files with changes

Staged: Files added and ready to commit

Unmodified: Files with no changes

Example Workflow

# 1. Create or edit files
# 2. Check changes
git status

# 3. Stage files
git add .

# 4. Commit changes
git commit -m "Your message"

# 5. Push to GitHub
git push origin main



React Native 
* How to build apk
Ans: 
1. first create expo account on expo website
2. npm install -g eas-cli
3. eas login
4. eas build:configure
5. eas build -p android --profile preview [OR] eas build -p android --profile production 

----------------------
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

java -jar bundletool-all-1.17.1.jar build-apks --bundle=application-07993c7b-460d-464f-932a-6c943c2faa60.aab --output=rentalx.apks --mode=universal --ks=my-release-key.keystore --ks-key-alias=my-key-alias --ks-pass=pass:sanjay@123 --key-pass=pass:sanjay@123












Things need to build app

npx expo prebuild --skip-dependency-update react-native,react

npm install -g eas-cli

eas login

eas build:configure

eas build --platform android

eas build --platform android --profile production

expo apk covert using jar =========== java -jar bundletool.jar build-apks --bundle=filename.aab --output=newfilename.apks --mode=universal

real command ============= java -jar bundletool-all-1.17.1.jar build-apks --bundle=application-87e11464-b949-40a3-86ad-e7658361cee3.aab --output=rentalx.apks --mode=universal

--------------

first create expo account on expo website
npm install -g eas-cli
eas login
eas build:configure
eas build -p android --profile preview [OR] eas build -p android --profile production

----------------------
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

Enter Valid Information
Provide valid inputs for the distinguished name (DN). If you want to skip a field, type a dot (.) and press ENTER. Here is an example sequence:

First and Last Name: e.g., Sanjay Kumar
Organizational Unit: e.g., IT Department
Organization Name: e.g., Bytegrow Technologies
City or Locality: e.g., Jaipur
State or Province: e.g., Rajasthan
Country Code: e.g., IN (use a valid two-letter country code)

java -jar bundletool-all-1.17.1.jar build-apks --bundle=application-b1a2c2f0-1752-4b4f-ae67-88626aed2231.aab --output=rentalx.apks --mode=universal --ks=my-release-key.keystore --ks-key-alias=my-key-alias --ks-pass=pass:sanjay@123 --key-pass=pass:sanjay@123



photo upload edit page code
@extends('layout.default')
@section('title', 'Edit Profile')
@section('content')
<style>
.image-exist.active { display: none; }
.select2-container .select2-selection--single { width: 100%; padding: 0.90rem 0.75rem; border: 1px solid #e5e7eb; border-radius: 6px; font-size: 1rem; color: #374151; outline: none; height: auto; display: flex; align-items: center;}
.select2-container--default .select2-selection--single .select2-selection__arrow { height: 50px !important; }
.select2.select2-container.select2-container--default{ width: 100% !important;}
.select2-container .select2-selection--single{ height: 50px !important; }
.select2-dropdown { border: 1px solid #e5e7eb; border-radius: 10px 0px; font-size: 1rem; color: #374151; }
</style>
@php
$company_logo_id = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'CompanyLogoId');
$company_logo = \App\Helpers\CommonHelper::getPhotoById($company_logo_id);
$name = Auth::user()->name;
$mobile = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'mobile');
$company_name = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'company_name');
$email = Auth::user()->email;
$state = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'state');
$city = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'city');
$street_name = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'street_name');

@endphp
<div class="w-full max-w-[800px]">
    <div class="flex justify-between items-center pb-5 py-5 mt-14 md:px-2">
            <div class="list-header">
                <div class="flex items-center justify-start">
                    <a href="{{route('client.project.list')}}" class="p-1"><img src="{{asset('public/images/arrow.svg')}}" alt="Back Button"></a>
                    <h2 class="font-normal text-2xl">Edit Profile</h2>
                </div>
            </div>
            <div class="list-header">
                <div class="flex items-center justify-center -mx-1.5">
                    <a href="{{ route('client.profile.view', Auth::user()->id) }}"
                        class="bg-[#F3EAFD] inline-flex items-center justify-center w-[30px] h-[30px] rounded-[20px] mx-1.5">
                        <img src="{{ asset('public/images/d_eye_icon.svg') }}" alt="View Icon" class="max-w-[16px]">
                        </a>
                </div>
        </div>
    </div>

    <div class="w-full p-8 md:p-3 bg-white rounded-md">
        <form action="{{route('client.profile.edit.post',Auth::user()->id)}}" method="post" class="flex flex-col"
            onsubmit="return checkForm();">
            @csrf
            <input type="hidden" id="CompanyLogoId" name="CompanyLogoId" value="{{$company_logo_id}}">
            <!-- Basic Information Section -->
            <div class="basic-information">
                <div class="mb-6 text-left">
                    <h3 class="text-[1.3rem] font-bold text-gray-700">Basic Information</h3>
                </div>

                <!-- Company Logo Upload -->
                <div class="input-group w-full mb-4 md:mb-2">
                    <!-- Dummy Preview -->
                    <div id="imagePreviewWrapper" class="mb-[30px] mt-[10px] items-center gap-[10px] {{ isset($company_logo->url) ? 'flex' : 'hidden' }}">
                        <div id="mainImageContainer" class="mb-[10px]">
                            @if(isset($company_logo->url))
                            <div class="image-preview-container w-auto rounded-md border border-gray-300 inline-block">
                                <div class="image-wrapper p-[0.30rem]">
                                    <img id="imagePreview" src="{{ $company_logo->url }}" alt="Company Logo" class="w-[150px] h-[150px] rounded-md object-contain block m-0 p-0" />
                                </div>
                                <div class="remove-button-wrapper">
                                    <button type="button" id="removeImageBtn" class="px-2.5 py-1 bg-red-600 text-white border-none cursor-pointer w-full mt-1">Remove</button>
                                </div>
                            </div>
                            @endif
                        </div>
                    </div>
                    
                </div>

                <div class="input-group w-full mb-4 md:mb-2 image-exist {{ isset($company_logo->url) ? 'active' : '' }}">
                    <p class="text-sm text-gray-600 mb-2">Company Logo</p>
                    <label for="company_logo" class="text-sm text-gray-600 mb-2 block">
                        <div class="w-full max-w-[180px] h-[150px] border-2 border-dashed border-gray-300 rounded-lg flex flex-col items-center justify-center text-center cursor-pointer bg-gray-100 transition-all duration-300 ease-in-out hover:border-gray-400">
                            <img src="{{ asset('public/images/upload_img1.svg') }}" alt="Upload" class="w-[50px] h-[50px] mb-2">
                            <p class="text-[14px] text-gray-700">Click to Upload</p>
                        </div>
                        <input type="file" name="company_logo" id="company_logo" accept=".png, .webp, .jpeg, .jpg" class="p-2 border border-gray-300 rounded-md text-base w-full hidden cursor-pointer" />
                    </label>
                </div>


                 <div class="flex justify-between gap-2 md:mb-2 md:flex-col">
                    <!-- Name -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="name" class="text-sm text-gray-600 mb-2 block">Name<span class="mandatory">*</span></label>
                        <input type="text" name="name" id="name" class="w-full p-3 border border-gray-300 rounded-md text-base text-gray-700 outline-none required_fields" value="{{$name}}"
                            data-error-msg="Name is required" />
                        <span class="scrollForReq error-message"></span>
                    </div>
                    <!-- Mobile -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="mobile" class="text-sm text-gray-600 mb-2 block">Mobile<span class="mandatory">*</span></label>
                        <input type="text" name="mobile" id="mobile" class="w-full p-3 border border-gray-300 rounded-md text-base text-gray-700 outline-none required_fields phone_validation"
                        value="{{$mobile}}" data-error-msg="Mobile is required" />
                        <span class="scrollForReq error-message"></span>
                    </div>
                </div>

                <div class="flex justify-between gap-2 md:mb-2 md:flex-col">
                    <!-- Company Name -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="company_name" class="text-sm text-gray-600 mb-2 block">Company Name</label>
                        <input type="text" name="company_name" id="company_name" class="w-full p-3 border border-gray-300 rounded-md text-base text-gray-700 outline-none"
                            value="{{ old('company_name', $company_name) }}" />
                    </div>

                    <!-- Email -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="email" class="text-sm text-gray-600 mb-2 block">Email<span class="mandatory">*</span></label>
                        <input type="text" name="email" id="email" class="w-full p-3 border border-gray-300 rounded-md text-base text-gray-700 outline-none required_fields email_validation"
                        value="{{$email}}" data-error-msg="Email is required" />
                        <span class="scrollForReq error-message"></span>
                    </div>
                </div>
            </div>

            <!-- Address Section -->
            <div class="address-information">
                <div class="mb-6 text-left">
                    <h3 class="text-[1.3rem] font-bold text-gray-700">Address</h3>
                </div>

                <div class="flex justify-between gap-2 md:mb-2 md:flex-col">
                    <!-- State -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="state" class="text-sm text-gray-600 mb-2 block">State</label>
                        <select name="state" id="state" class="border border-gray-300 rounded-md text-base text-gray-700 outline-none">
                            <option value="">Select State</option>
                            @foreach($getStates as $value)
                            <option value="{{ $value->state }}" @if($state==$value->state) selected @endif>{{
                                $value->state }}</option>
                            @endforeach
                        </select>
                    </div>

                    <!-- City -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="city" class="text-sm text-gray-600 mb-2 block">City</label>
                        <select name="city" id="city" class="border border-gray-300 rounded-md text-base text-gray-700 outline-none" required disabled>
                            <option value="{{ $city ?? '' }}">{{ $city ?: 'Select City' }}</option>
                        </select>
                    </div>
                </div>
                <div class="flex justify-between gap-2 md:mb-2 md:flex-col">
                    <!-- Street Name -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="street_name" class="text-sm text-gray-600 mb-2 block">Street Name</label>
                        <input type="text" name="street_name" id="street_name" class="w-full p-3 border border-gray-300 rounded-md text-base text-gray-700 outline-none" value="{{$street_name}}" />
                    </div>

                    <!-- Password -->
                    <div class="input-group w-1/2 mb-4 md:mb-2 md:w-full">
                        <label for="password" class="text-sm text-gray-600 mb-2 block">Change Password</label>
                        <input type="password" name="password" id="password" class="w-full p-3 border border-gray-300 rounded-md text-base text-gray-700 outline-none" autocomplete="new-password" />

                        <div class="py-2 flex items-center gap-2">
                            <input type="checkbox" id="show-hide-btn" class="!w-[15px] !h-[15px] cursor-pointer border border-gray-300 rounded-md text-base text-gray-700 outline-none"/>
                            <label for="show-hide-btn" class="text-sm text-gray-600 cursor-pointer !mb-0">
                                Show password
                            </label>
                        </div>
                        
                    </div>
                </div>
            </div>

         <div class="w-full">
            <!-- Submit Button -->
            <button type="submit" class="p-[0.95rem] bg-gray-700 text-white text-base border-none rounded-md cursor-pointer transition-all duration-300 mt-4 mb-4 w-full uppercase">UPDATE</button>
        </div>
        </form>
    </div>
</div>


<!-- Scripts -->
<script>
    const showHideBtn = document.getElementById('show-hide-btn');
    const passwordField = document.getElementById('password');

    showHideBtn.addEventListener('change', function () {
        if (this.checked) {
            passwordField.type = 'text';
        } else {
            passwordField.type = 'password';
        }
    });

    // upload artwork image start

    var fileTypesBusLicense = ['jpg', 'jpeg', 'png', 'JPG', 'JPEG', 'PNG', 'webp', 'WEBP'];

    $("#company_logo").on('change', function (e) {
        if ($(this).val() != '') {
            var that = this;
            if (this.files && this.files[0]) {
                var fsize = this.files[0].size;
                const file = Math.round((fsize / 1024));
                if (file >= 10240) {
                    Swal.fire({
                        title: 'Image size is too big, please upload less then 10MB size',
                        icon: 'warning',
                        showCancelButton: false,
                        confirmButtonText: 'OK',
                        customClass: {
                            popup: '',
                            title: '',
                            actions: '',
                        },

                    }).then(response => {
                        if (!response.ok) {
                        }
                        return response.json();
                    });
                }
                var extension = this.files[0].name.split('.').pop().toLowerCase(),
                    isSuccess = fileTypesBusLicense.indexOf(extension) > -1;
                if (isSuccess) {
                    upload(this, extension);
                } else {
                    Swal.fire({
                        title: 'Invalid file format, only upload (JPG, JPEG, PNG, WEBP) formats',
                        icon: 'warning',
                        showCancelButton: false,
                        confirmButtonText: 'OK',
                        customClass: {
                            popup: '',
                            title: '',
                            actions: '',
                        },

                    }).then(response => {
                        if (!response.ok) {
                        }
                        return response.json();
                    });
                }
            }
            e.target.value = '';
        }
    });

    function upload(img, extension) {
    var form_data = new FormData();
    form_data.append('photo', img.files[0]);
    form_data.append('_token', '{{ csrf_token() }}');

    $('.overlay').addClass('active');
    $('body').addClass('overlay_section');
    $(".acoda-spinner").css("display", "inline-flex");

    jQuery.ajax({
        url: "{{ route('client.company.logo.upload') }}",
        data: form_data,
        type: 'POST',
        contentType: false,
        processData: false,
        success: function (data) {
            if (!data.errors) {
                $('#imagePreviewWrapper').show();
                $('.image-preview-container').remove();
                $('.image-exist').addClass('active');

                $("#imagePreview").attr('src', '');
                $("#CompanyLogoId").val('');
                $("#CompanyLogoId").val(data.imageId);
                $("#imagePreview").attr('src', data.miniImageUrl);

                $('#mainImageContainer').append(`
                    <div class="image-preview-container inline-block w-auto rounded-md border border-gray-300">
                        <div class="image-wrapper p-[0.30rem]">
                            <img id="imagePreview" src="${data.miniImageUrl}" alt="Company Logo" class="w-[150px] h-[150px] rounded-md object-contain block m-0 p-0" />
                        </div>
                        <div class="remove-button-wrapper">
                            <button type="button" id="removeImageBtn" class="w-full mt-1 px-2.5 py-1 bg-red-600 text-white text-sm rounded-md cursor-pointer">Remove</button>
                        </div>
                    </div>
                `);
            } else {
                Swal.fire({
                    title: 'File format not supported. Please upload a PNG, JPG or WEBP file',
                    icon: 'warning',
                    confirmButtonText: 'OK',
                });
            }
        },
        complete: function () {
            $('#imagePreview').on('load', function () {
                    $('.overlay').removeClass('active');
                    $('body').removeClass('overlay_section');
                    $(".acoda-spinner").css("display", "none");
                });
            },
            error: function (xhr, status, error) {
                console.error('Upload error:', error.message);
            }
        });
    }

    // Handle Remove Button Click
    $('body').on('click', '#removeImageBtn', function () {
        $('.image-exist').removeClass('active');
        $("#imagePreview").attr('src', '');
        $("#CompanyLogoId").val('');
        $('#imagePreviewWrapper').hide();
        $('.image-preview-container').remove();
    });

    // upload artwork image end

    // Validate form start
    function checkForm() {
        $('.overlay').addClass('active');
        $('body').addClass('overlay_section');
        $(".acoda-spinner").css("display", "inline-flex");

        let hasErrors = false;
        let firstErrorElement = null;

        $(".required_fields").each(function () {
            let $this = $(this);
            let value = $this.val().trim();
            let errorMessage = $this.data("error-msg");
            let errorContainer = $this.closest('.input-group').find('.error-message');

            if (!value) {
                hasErrors = true;
                if (!firstErrorElement) {
                    firstErrorElement = $this;
                }
                errorContainer.html(errorMessage);
            } else {
                errorContainer.empty();
            }

            // Mobile number validation (if applicable)
            if ($this.hasClass('phone_validation')) {
                let inputValue = $this.val().trim();
                if (!inputValue) {
                    hasErrors = true;
                    errorContainer.html("Mobile number is required");
                } else if (inputValue.length < 10) {
                    hasErrors = true;
                    errorContainer.show().html("Mobile number must be at least 10 digits");
                } else {
                    errorContainer.empty();
                }
            }

            // Email validation (if applicable)
            if ($this.hasClass('email_validation')) {
                let inputValue = $this.val().trim();
                let emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/; // Standard email validation pattern

                if (!inputValue) {
                    hasErrors = true;
                    errorContainer.text("Email is required").show();
                } else if (!emailPattern.test(inputValue)) {
                    hasErrors = true;
                    errorContainer.text("Enter a valid email address").show();
                } else {
                    errorContainer.hide();
                }
            }

        });

        if (hasErrors) {
            hideLoader();
            Swal.fire({
                title: 'Please fill all required fields',
                icon: 'warning',
                confirmButtonText: 'OK'
            }).then(() => {
                if (firstErrorElement) {
                    $("html, body").animate({
                        scrollTop: firstErrorElement.offset().top - 150
                    }, 500);
                }
            });
            return false;
        }

        console.log('Validation successful!');
        return true;
    }

    // Validate form end
    function hideLoader() {
        $('.overlay').removeClass('active');
        $('body').removeClass('overlay_section');
        $(".acoda-spinner").css("display", "none");
    }

    $('.required_fields').on('keyup', function () {
        let $inputGroup = $(this).closest('.input-group');
        let errorMessage = $inputGroup.find('.error-message');
        let errorIcon = $inputGroup.find('.error');

        if (!$(this).val().trim()) {
            errorMessage.text($(this).data("error-msg")).show();
            errorIcon.hide();
        } else {
            errorMessage.hide();
            errorIcon.hide();
        }
    });


    $(document).ready(function () {
        $('#state, #city').select2();
    });

    $('body').on('change', '#state', function () {
        const stateName = $(this).val();
        const citySelect = $('#city');

        if (stateName) {
            citySelect.prop('disabled', true).empty().append('<option>Loading...</option>');

            $.ajax({
                url: "{{ route('client.getCitiesByState') }}",
                method: 'POST',
                data: {
                    stateName: stateName,
                    "_token": "{{ csrf_token() }}"
                },
                success: function (response) {
                    citySelect.prop('disabled', false).empty();

                    if (response.message && response.message === 'No data found') {
                        citySelect.append('<option value="">No data found</option>');
                    } else {
                        citySelect.append('<option value="">Select City</option>');
                        response.forEach(city => {
                            citySelect.append(`<option value="${city}">${city}</option>`);
                        });
                    }

                    citySelect.select2();
                },
                error: function () {
                    citySelect.prop('disabled', false).empty().append('<option>Error fetching cities</option>');
                }
            });
        } else {
            citySelect.prop('disabled', true).empty().append('<option value="">Select City</option>');
        }
    });

</script>
@endsection 

view page code
@extends('layout.default')
@section('title', 'View Profile')

@section('content')
@php
$company_logo_id = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'CompanyLogoId');
$company_logo = \App\Helpers\CommonHelper::getPhotoById($company_logo_id);
$name = Auth::user()->name;
$mobile = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'mobile');
$company_name = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'company_name');
$email = Auth::user()->email;
$state = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'state');
$city = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'city');
$street_name = App\Helpers\CommonHelper::getUserMeta(Auth::user()->id, 'street_name');
@endphp


<div class="w-full max-w-4xl mt-16">
    @if (session('success'))
        <div class="flex items-center gap-2 p-3 my-3 text-sm font-bold text-green-800 bg-green-100 border border-green-300 rounded-md alert">
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="10" stroke="green" stroke-width="2"/><path d="M7 12l3 3 7-7" stroke="green" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
            {{ session('success') }}
        </div>
    @endif

    @if (session('error'))
        <div class="flex items-center gap-2 p-3 my-3 text-sm font-bold text-red-800 bg-red-100 border border-red-300 rounded-md alert">
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="10" stroke="red" stroke-width="2"/><path d="M8 8l8 8M16 8l-8 8" stroke="red" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
            {{ session('error') }}
        </div>
    @endif
    <div class="flex justify-between items-center py-5 md:px-3">
        <div class="flex items-center gap-2">
            <a href="{{ route('client.profile.edit', Auth::user()->id) }}" class="p-1">
                <img src="{{ asset('public/images/arrow.svg') }}" alt="Back Button">
            </a>
            <h2 class="text-2xl font-normal">View Profile</h2>
        </div>
        <a href="{{ route('client.profile.edit', Auth::user()->id) }}" class="bg-[#EBF0F9] w-[30px] h-[30px] flex items-center justify-center rounded-full">
            <img src="{{ asset('public/images/icons_edit.svg') }}" alt="Edit Icon" class="w-4 h-4">
        </a>
    </div>

    <div class="w-full p-8 lg:p-4 bg-white rounded-md shadow-sm">
        <div class="mb-8">
            <h3 class="text-lg font-bold text-gray-700 mb-4">Basic Information</h3>
    
            @if(!empty($company_logo_id))
            <div class="mb-6">
                <p class="text-sm font-medium text-gray-700 mb-1">Company Logo</p>
                <div class="w-fit border border-gray-200 p-2 rounded-md">
                    <img src="{{ $company_logo->url }}" alt="Company Logo" class="w-36 h-36 object-contain rounded-md">
                </div>
            </div>
            @endif
    
            <div class="w-full">
                <div class="flex min-w-[250px] lg:flex items-center lg:w-full">
                    <div class="w-1/2 mb-4">
                        <p class="text-sm text-gray-600 mb-1">Name</p>
                        <p class="text-sm text-black-600 mb-1">{{ $name }}</p>
                    </div>
    
                    @if(!empty($mobile))
                    <div class="w-1/2 mb-4">
                        <p class="text-sm text-gray-600 mb-1">Mobile</p>
                        <p class="text-sm text-black-600 mb-1">{{ $mobile }}</p>
                    </div>
                    @endif
                </div>
    
                <div class="flex min-w-[250px] lg:flex items-center lg:w-full">
                    @if(!empty($company_name))
                    <div class="w-1/2 mb-4">
                        <p class="text-sm text-gray-600 mb-1">Company Name</p>
                        <p class="text-sm text-black-600 mb-1">{{ $company_name }}</p>
                    </div>
                    @endif
    
                    <div class="w-1/2 mb-4">
                        <p class="text-sm text-gray-600 mb-1">Email</p>
                        <p class="text-sm text-black-600 mb-1">{{ $email }}</p>
                    </div>
                </div>
            </div>
        </div>
    
        @if(!empty($state) || !empty($city) || !empty($street_name))
        <div class="w-full">
            <h3 class="text-lg font-bold text-gray-700 mb-4">Address</h3>
            <div class="w-full">
                <div class="flex min-w-[250px] lg:flex items-center lg:w-full">
                    @if(!empty($state))
                    <div class="w-1/2 mb-4">
                        <p class="text-sm text-gray-600 mb-1">State</p>
                        <p class="text-sm text-black-600 mb-1">{{ $state }}</p>
                    </div>
                    @endif
    
                    @if(!empty($city))
                    <div class="w-1/2 mb-4">
                        <p class="text-sm text-gray-600 mb-1">City</p>
                        <p class="text-sm text-black-600 mb-1">{{ $city }}</p>
                    </div>
                    @endif
                </div>
    
                <div class="flex min-w-[250px] lg:flex items-center lg:w-full">
                    @if(!empty($street_name))
                    <div class="w-1/2 mb-4">
                        <p class="text-sm text-gray-600 mb-1">Street Name</p>
                        <p class="text-sm text-black-600 mb-1">{{ $street_name }}</p>
                    </div>
                    @endif
                </div>
            </div>
        </div>
        @endif
    </div>
</div>

<script>
    setTimeout(() => {
        document.querySelectorAll('.alert').forEach(alert => {
            alert.style.display = 'none';
        });
    }, 3000);
</script>
@endsection

controller code 
<?php
namespace App\Http\Controllers\Web\Client;
use App\Http\Controllers\Controller;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\DB;
use Illuminate\Support\Facades\Session;
use Auth;
use Hash;
use Helper;
use App\Models\Projects;
use App\Models\User;
use App\Models\UserMetas;
use App\Models\master_images;
use App\Models\States;
use Intervention\Image\Facades\Image;
use Illuminate\Support\Facades\Validator;
class SettingController extends Controller
{
     public function Edit($id){
        $getStates = States::select('state')->distinct()->get();
        return view('pages.client.settings.edit',compact('getStates'));
     }
     
     public function View($id){
        $getStates = States::select('state')->distinct()->get();
        return view('pages.client.settings.view',compact('getStates'));
     }

     public function EditPost(Request $request, $id){
  
        $messages = [
            'name.required' => 'Name is required.',
            'mobile.required' => 'Mobile number is required.',
            'mobile.numeric' => 'Mobile number must be numeric.',
            'email.required' => 'Email is required.',
            'email.email' => 'Email must be a valid email address.',
        ];
    
        $validator = Validator::make($request->all(), [
            'name' => 'required',
            'mobile' => 'required|numeric',
            'email' => 'required|email', 
        ], $messages);
    
        if ($validator->fails()) {
            return redirect()->back()->withErrors($validator)->withInput();
        }
    
        $user = User::where('id', $id)->where('status', '!=', 'inactive')->first();
    
        if (!$user) {
            return redirect()->back()->with('error', 'User not found or inactive.');
        }

        $updateData = [
            'name' => $request->name,
            'email' => $request->email,
        ];
    
        if (!empty($request->password)) {
            $updateData['password'] = Hash::make($request->password);
        }

        User::where('id', $id)->update($updateData);
    
        $metaFields = ['CompanyLogoId', 'mobile', 'company_name', 'state', 'city', 'street_name'];
        foreach ($metaFields as $field) {
            $this->insertOrUpdateUsermeta($user->id, $field, $request->$field ?? null);
        }
    
        return redirect()->route('client.profile.view', $id)->with('success', 'Profile updated successfully.');
     }   

     public function CompanyLogoUpload(Request $request){
        $image=$request->photo;
        $name=$image->getClientOriginalName();
        $mimeType=$image->getMimeType();
        $name=time().$name;
        $validator = Validator::make($request->all(), [
            'photo' => 'required|mimes:jpeg,jpg,png,webp,PNG,JPG,JPEG,WEBP|max:10240'
       ]);
       if ($validator->fails())
       {
          return response()->json(['errors'=>$validator->errors()->all(),'success'=>false,'error'=>true]);
       }
       else
       {
        if(!file_exists(public_path().'/uploads/'))
        {
            mkdir(public_path().'/uploads/');
        }
        if(!file_exists(public_path().'/uploads/companyLogo'))
        {
            mkdir(public_path().'/uploads/companyLogo');
        }
        if(!file_exists(public_path().'/uploads/companyLogo/'))
        {
            mkdir(public_path().'/uploads/companyLogo/');
        }
        if (!file_exists(public_path().'/uploads/companyLogo/172x172/')) {

            mkdir(public_path().'/uploads/companyLogo/172x172/');

        }
        $miniImageUrl = url('/').'/uploads/companyLogo/'.$name;
        $imageObjectMini = false;
        try{
            $image=$request->file('photo');
            $image_resize = Image::make($image->getRealPath());
            $image_resize->save(public_path().'/uploads/companyLogo/172x172/'.$name,100);
            $miniImageUrl = url('/').'/public/uploads/companyLogo/172x172/'.$name;
            $imageObjectMini=master_images::create(['name'=>$image->getClientOriginalName(),'url'=>url('/').'/public/uploads/companyLogo/172x172/'.$name,'base_url'=>public_path().'/uploads/companyLogo/172x172/'.$name,'withoutPublicUrl'=>'/uploads/companyLogo/172x172/'.$name]);
        }
        catch(\Exception $e){
        }
        catch(NotSupportedException $e){
        }
        catch(ImageException $e){
        }
       catch(InvalidArgumentException $e){
      }
      catch(MissingDependencyException $e){
      }
      catch(NotFoundException $e){
      }
      catch(NotReadableException $e){
      }
      catch(NotWritableException $e){
      }
      catch(RuntimeException $e){
      }
      $image->move(public_path().'/uploads/companyLogo/',$name);
      $imageObject=master_images::create(['name'=>$image->getClientOriginalName(),'url'=>url('/').'/public/uploads/companyLogo/',$name,'base_url'=>public_path().'/uploads/companyLogo/'.$name,'withoutPublicUrl'=>'/uploads/companyLogo/'.$name]);
      return response()->json(['success'=>true,'imageId'=>($imageObjectMini)?$imageObjectMini->id:$imageObject->id,'imageUrl'=>url('/').'/public/uploads/companyLogo/'.$name,'miniImageUrl'=>$miniImageUrl]);
     }
  }
}



master images model 
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class master_images extends Model
{
    use HasFactory;
    protected $fillable = [
        'name',
        'url',
        'base_url',
        'status',
        'ImageUniqueId',
        'withoutPublicUrl'
    ];

    /**
     * The attributes that should be hidden for serialization.
     *
     * @var array<int, string>
     */
    protected $table = 'master_images';
    protected $hidden = [
        'created_at','updated_at'
       ];
}

master images table code
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('master_images', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->text('url');
            $table->text('base_url');
            $table->text('withoutPublicUrl')->nullable();
            $table->text('ImageUniqueId')->nullable();
            $table->enum('status',['active','inactive'])->nullable()->default('active');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('master_images');
    }
};


user metas model code

<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class UserMetas extends Model
{
    use HasFactory;
    protected $fillable = [
        'userId',
        'meta_key',
        'meta_value',
        'status'
    ];

    /**
     * The attributes that should be hidden for serialization.
     *
     * @var array<int, string>
     */
    protected $table = 'user_metas';
    protected $hidden = [
        'created_at','updated_at'
       ];
}

user metas table code
 <?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('user_metas', function (Blueprint $table) {
            $table->id();
            $table->integer('userId');
            $table->text('meta_key');
            $table->text('meta_value');
            $table->enum('status',['active','inactive'])->nullable()->default('active');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('user_metas');
    }
};


base controller code 
<?php

namespace App\Http\Controllers;
use App\Models\UserMetas;

use Illuminate\Foundation\Auth\Access\AuthorizesRequests;
use Illuminate\Foundation\Bus\DispatchesJobs;
use Illuminate\Foundation\Validation\ValidatesRequests;
use Illuminate\Routing\Controller as BaseController;

class Controller extends BaseController
{
    use AuthorizesRequests, DispatchesJobs, ValidatesRequests;

    protected function insertOrUpdateUsermeta($userId,$userMetaKey,$userMetaValue)
    {
        if(strcmp($userMetaValue,'')!=0)
        {
            UserMetas::updateOrCreate(['userId'=>$userId,'meta_key'=>$userMetaKey],['partnerId'=>$userId,'meta_key'=>$userMetaKey,'meta_value'=>$userMetaValue]);
        }
        elseif(strcmp($userMetaValue,'')==0){
          $userMetaValue = '';
          UserMetas::updateOrCreate(['userId'=>$userId,'meta_key'=>$userMetaKey],['partnerId'=>$userId,'meta_key'=>$userMetaKey,'meta_value'=>$userMetaValue]);
        }
        
    }

}


helper code 
<?php
namespace App\Helpers;
use App\Models\User;
use App\Models\UserMetas;
use App\Models\master_images;
use Illuminate\Support\Facades\Auth;
use DB;
class CommonHelper
{
 

    public static function getUserRole($userId)
    {
        $user = User::with('roles')->find($userId);
        if (!$user) {
            return 'User not found';
        }
        return $user->roles->pluck('name')->implode(', '); 
    }
    

   public static function getUserMeta($userId,$userMetaKey){
        $UserMetas=UserMetas::where([['userId','=',$userId],['meta_key','LIKE',$userMetaKey]])->first();
        return ($UserMetas)?$UserMetas->meta_value:'';
   }

   public static function getPhotoById($imageId)
   {
       return master_images::whereId($imageId)->first();
   }

    public static function getUserRoleName($userRole){
        if ($userRole) {
            $roleName = $userRole->name;
            return $roleName;
        }
    }

     public static function getTimeAgo($carbonObject) {
        return str_ireplace(
            [' seconds', ' second', ' minutes', ' minute', ' hours', ' hour', ' days', ' day', ' weeks', ' week'],
            ['s', 's', 'm', 'm', 'h', 'h', 'd', 'd', 'w', 'w'],
            $carbonObject->diffForHumans()
        );
    }

    public static function getUsernameById($userId)
    {
        $user = User::find($userId);
        return $user ? $user->name : 'User not found';
    }
}
?>




admin middleware code 
<?php

namespace App\Http\Middleware;
use App\Models\User;
use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;
use Symfony\Component\HttpFoundation\Response;

class AdminMiddleware
{
    /**
     * Handle an incoming request.
     *
     * @param  \Closure(\Illuminate\Http\Request): (\Symfony\Component\HttpFoundation\Response)  $next
     */
    public function handle(Request $request, Closure $next): Response
    {
        if (Auth::check()) {
            $userId = auth()->user()->id;
            $userStatus = auth()->user()->status;
            if(strcmp($userStatus,'inactive')==0){
                Auth::guard('web')->logout();
                return redirect()->route('login');
            }else{
                $user = User::whereId($userId)->with('roles')->first();
                $role = 'admin';
                if (isset($user->roles[0]->name)) {
                    $role = $user->roles[0]->name;
                }
                if (strcmp($role, 'admin') == 0) {
                    return $next($request);
                } else {
                    return redirect()->route('client.dashboard')->with('message', 'You are not an authorised user');
                }
            }  
           } else {
            Auth::guard('web')->logout();
            return redirect()->route('login');
          } 
    }
}

client middleware code 
<?php

namespace App\Http\Middleware;
use App\Models\User;
use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Auth;
use Symfony\Component\HttpFoundation\Response;

class ClientMiddleware
{
    /**
     * Handle an incoming request.
     *
     * @param  \Closure(\Illuminate\Http\Request): (\Symfony\Component\HttpFoundation\Response)  $next
     */
    public function handle(Request $request, Closure $next): Response
    {
        if (Auth::check()) {
            $userId = auth()->user()->id;
            $userStatus = auth()->user()->status;
            if(strcmp($userStatus,'inactive')==0){
                Auth::guard('web')->logout();
                return redirect()->route('login');
            }else{
                $user = User::whereId($userId)->with('roles')->first();
                $role = 'client';
                if (isset($user->roles[0]->name)) {
                    $role = $user->roles[0]->name;
                }
                if (strcmp($role, 'client') == 0) {
                    return $next($request);
                } else {
                    return redirect()->route('admin.dashboard')->with('message', 'You are not an authorised user');
                }
            }  
           } else {
            Auth::guard('web')->logout();
            return redirect()->route('login');
          } 
    }
}


web.php code 
<?php
use Illuminate\Support\Facades\Route;

Route::fallback(function () {
    return redirect('/');
});

// Select Option For City & State

Route::post('/logout', [App\Http\Controllers\Web\Auth\AuthController::class, 'LogOut'])->name('logout');
Route::post('/import/riskcategories', [App\Http\Controllers\Web\Public\PublicController::class, 'importRiskCategories'])->name('import.riskcategories');

Route::middleware(['guest'])->group(function () {
    Route::get('/', [App\Http\Controllers\Web\Public\PublicController::class, 'index']);
    Route::get('/welcome', [App\Http\Controllers\Web\Public\PublicController::class, 'welcome']);
    Route::get('/login', [App\Http\Controllers\Web\Auth\AuthController::class, 'Login'])->name('login');
    Route::post('/login/post', [App\Http\Controllers\Web\Auth\AuthController::class, 'LoginPost'])->name('login.post');
    // Route::get('/register', [App\Http\Controllers\Web\Auth\AuthController::class, 'Register'])->name('register');
    // Route::post('/register/post', [App\Http\Controllers\Web\Auth\AuthController::class, 'RegisterPost'])->name('register.post');
    Route::post('/company/logo/upload', [App\Http\Controllers\Web\Auth\AuthController::class, 'CompanyLogoUpload'])->name('company.logo.upload');
    Route::get('/accept-invitation/{token}', [App\Http\Controllers\Web\Admin\ClientController::class, 'showAcceptForm'])->name('accept-invitation');
    Route::post('/accept-invitation/{token}', [App\Http\Controllers\Web\Admin\ClientController::class, 'handleAccept'])->name('accept-invitation.token');

});





Route::group(
    [
        'prefix' => 'admin',
        'as' => 'admin.',
        'middleware' => [
            'auth',
            'isAdmin'
        ],
    ],
    function () {
        // Dashboard
        Route::get('/dashboard', [App\Http\Controllers\Web\Admin\DashboardController::class, 'Dashboard'])->name('dashboard');

        // Clients
        Route::get('/client/list', [App\Http\Controllers\Web\Admin\ClientController::class, 'ClientList'])->name('client.list');
        Route::get('/client/add', [App\Http\Controllers\Web\Admin\ClientController::class, 'ClientAdd'])->name('client.add');
        Route::post('/client/add/post', [App\Http\Controllers\Web\Admin\ClientController::class, 'ClientAddPost'])->name('client.add.post');
        Route::get('/client/edit/{id}', [App\Http\Controllers\Web\Admin\ClientController::class, 'ClientEdit'])->name('client.edit');
        Route::post('/client/edit/post/{id}', [App\Http\Controllers\Web\Admin\ClientController::class, 'ClientEditPost'])->name('client.edit.post');
        Route::get('/client/view/{id}', [App\Http\Controllers\Web\Admin\ClientController::class, 'ClientView'])->name('client.view');
        Route::post('/client/delete/post/{id}', [App\Http\Controllers\Web\Admin\ClientController::class, 'ClientDelete'])->name('client.delete.post');
        Route::post('/company/logo/upload', [App\Http\Controllers\Web\Admin\ClientController::class, 'CompanyLogoUpload'])->name('company.logo.upload');

        // Projects
        Route::get('/project/list', [App\Http\Controllers\Web\Admin\ProjectController::class, 'ProjectList'])->name('project.list');
        Route::get('/project/edit/{id}', [App\Http\Controllers\Web\Admin\ProjectController::class, 'ProjectEdit'])->name('project.edit');
        Route::post('/project/edit/post/{id}', [App\Http\Controllers\Web\Admin\ProjectController::class, 'ProjectEditPost'])->name('project.edit.post');
        Route::get('/project/view/{id}', [App\Http\Controllers\Web\Admin\ProjectController::class, 'ProjectView'])->name('project.view');
        Route::get('/project/artwork/{id}', [App\Http\Controllers\Web\Admin\ProjectController::class, 'ProjectArtwork'])->name('project.artwork');
        Route::post('/store-table-data', [App\Http\Controllers\Web\Admin\ArtworkController::class, 'storeTableData'])->name('store.table_data');
        Route::get('/download-pdf/{id}', [App\Http\Controllers\Web\Admin\ArtworkController::class, 'generatePDF'])->name('download.pdf');
        Route::post('/project/artwork/upload', [App\Http\Controllers\Web\Admin\ProjectController::class, 'ArtworkImageUpload'])->name('project.artwork.upload');

        Route::get('/3D-builder', [App\Http\Controllers\Web\Admin\ProjectController::class, 'signBuilder'])->name('3D-builder');

        // Csv
        Route::get('/project/export-csv/{id}', [App\Http\Controllers\Web\Admin\ProjectController::class, 'exportProjectCSV'])->name('project.export.csv');

        Route::post('/get-cities', [App\Http\Controllers\Web\Admin\ProjectController::class, 'getCitiesByState'])->name('getCitiesByState');
        Route::post('/get/wind-snow', [App\Http\Controllers\Web\Admin\ProjectController::class, 'getWindSnowValueByCities'])->name('getWindSnowValueByCities');

        Route::post('/send-invitation', [App\Http\Controllers\Web\Admin\ClientController::class, 'sendInvitation'])->name('send.invitation');


        Route::get('/terms-and-conditions/edit', [App\Http\Controllers\Web\Admin\ClientController::class, 'editTermsAndConditions'])->name('terms.edit');
        Route::post('/terms-and-conditions/update', [App\Http\Controllers\Web\Admin\ClientController::class, 'updateTermsAndConditions'])->name('terms.update');
    }
);


Route::group(
    [
        'prefix' => 'client',
        'as' => 'client.',
        'middleware' => [
            'auth',
            'isClient'
        ],
    ],
    function () {

        // Dashboard
        Route::get('/dashboard', [App\Http\Controllers\Web\Client\DashboardController::class, 'Dashboard'])->name('dashboard');

        // Projects
        Route::get('/project/list', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectList'])->name('project.list');
        Route::get('/project/add', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectAdd'])->name('project.add');
        Route::post('/project/create/next', [App\Http\Controllers\Web\Client\ProjectController::class, 'create'])->name('project.create.next');
        Route::get('/project/calculation', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectCalculation'])->name('project.calculation');
        Route::post('/project/artwork/upload', [App\Http\Controllers\Web\Client\ProjectController::class, 'ArtworkImageUpload'])->name('project.artwork.upload');
        Route::post('/project/calculation/post', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectCalculationPost'])->name('project.calculation.post');
        Route::get('/project/edit/{id}', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectEdit'])->name('project.edit');
        Route::post('/project/edit/post/{id}', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectEditPost'])->name('project.edit.post');
        Route::get('/project/view/{id}', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectView'])->name('project.view');
        Route::get('/project/artwork/{id}', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectArtwork'])->name('project.artwork');
        Route::post('/store-table-data', [App\Http\Controllers\Web\Client\ArtworkController::class, 'storeTableData'])->name('store.table_data');
        Route::get('/download-pdf/{id}', [App\Http\Controllers\Web\Client\ArtworkController::class, 'generatePDF'])->name('download.pdf');
        Route::post('/project/delete/post/{id}', [App\Http\Controllers\Web\Client\ProjectController::class, 'ProjectDelete'])->name('project.delete.post');

        // 3D Sign 
        Route::get('/project/3d-sign/create', [App\Http\Controllers\Web\Client\ProjectController::class, 'createThreeDSign'])->name('project.3d-sign.create');
        Route::get('/3D-builder', [App\Http\Controllers\Web\Client\ProjectController::class, 'signBuilder'])->name('3D-builder');
        Route::get('/project/export-csv/{id}', [App\Http\Controllers\Web\Client\ProjectController::class, 'exportProjectCSV'])->name('project.export.csv');

        // Settings 
        Route::get('/profile/view/{id}', [App\Http\Controllers\Web\Client\SettingController::class, 'View'])->name('profile.view');
        Route::get('/profile/edit/{id}', [App\Http\Controllers\Web\Client\SettingController::class, 'Edit'])->name('profile.edit');
        Route::post('/profile/edit/post/{id}', [App\Http\Controllers\Web\Client\SettingController::class, 'EditPost'])->name('profile.edit.post');
        Route::post('/company/logo/upload', [App\Http\Controllers\Web\Client\SettingController::class, 'CompanyLogoUpload'])->name('company.logo.upload');

        Route::post('/get-cities', [App\Http\Controllers\Web\Client\ProjectController::class, 'getCitiesByState'])->name('getCitiesByState');
        Route::post('/get/wind-snow', [App\Http\Controllers\Web\Client\ProjectController::class, 'getWindSnowValueByCities'])->name('getWindSnowValueByCities');

        Route::get('/terms-and-conditions', [App\Http\Controllers\Web\Client\DashboardController::class, 'termsAndConditions'])->name('terms-and-conditions');
        Route::get('/download-terms-and-conditions', [App\Http\Controllers\Web\Client\DashboardController::class, 'downLoadtermsAndConditions'])->name('download.terms');

    }
);



