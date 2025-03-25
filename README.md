# basicgitsnippets
<br>
Author sanjayexplorer

<-----------git notes--------------->

git init globaly =>
git config --global user.name "Your New Name"
git config --global user.email "your.new.email@example.com"

how to check git init in system and git details =>
git config --global user.name
git config --global user.email

git add remote to access project from github profile =>
git remote add origin <repository_url>
example : git remote add origin https://github.com/sanjayexplorer/basicgitsnippets

clone a copy of project from github profile =>
git clone <repository_url>
example : git clone https://github.com/sanjayexplorer/basicgitsnippets

check hidden folder in project =>
git ls -a

how to check modified files in project =>
git status


how many status in git =>

untracked(new files that git does not yet track)

modified(changed files)

staged(files that ready to commit)

unmodified(unchanged)

-----map------

untracked(untracked files that new created )
                |
                |
                v
modified(changed files)
                |
                |
                v
staged(files that ready to commit)
                |
                |
                v
unmodified(unchanged)

create file
write in file
check how many files are changed (git status)
then add files to push in repo(git add .)
then commit(git commit -m 'comment')
git push
then check in repo






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





-----------------------------------------
 public function index(){
        $users = User::where('id', '!=', auth()->user()->id)
        ->whereIn('status', ['active', 'inactive'])
        ->where(function ($query) {
            $query->whereHas('roles', function ($q) {
                $q->where('name', 'LIKE', 'partner');
            })
            ->orWhereHas('roles', function ($q) {
                $q->where('name', 'LIKE', 'agent');
            });
        })
        ->with('roles')
        ->orderBy('created_at', 'DESC')
        ->get();
       return view('admin.users.list',compact('users'));
    }

    public function getUserListAjax(Request $request ){
        $draw = $request->get('draw');
        $start = $request->get("start");
        $rowPerPage= $request->get("length");
        $orderArray = $request->get('order');
        $columnNameArray = $request->get('columns');
        $searchArray = $request->get('search');
        $columnIndex = $orderArray[0]['column'];
        $columnName  = $columnNameArray[$columnIndex]['data'];
        $columnSortOrder = $orderArray[0]['dir'];
        $searchValue = $searchArray['value'];
        $adminId=auth()->user()->id;
        //'orderArray',$columnSortOrder,
        // dd('columnNameArray:',$columnNameArray, 'columnIndex:',$columnIndex,'columnName:',$columnName,'columnSortOrder:',$columnSortOrder);
        $users = User::where('id','!=',auth()->user()->id)
        ->whereIn('status', ['active', 'inactive'])
        ->where(function ($query) {
            $query->whereHas('roles', function ($q) {
                $q->where('name', 'LIKE', 'partner');
            })
            ->orWhereHas('roles', function ($q) {
                $q->where('name', 'LIKE', 'agent');
            });
        })
        ->with('roles')
        ->orderbydesc('created_at')->get([ 'id','mobile','created_at','status']);

        $total = $users->count();
        $users = $users->sortBy($columnName, SORT_REGULAR, $columnSortOrder)->slice($start, $rowPerPage);

        $arrData = collect([]);
        foreach ($users as $user) {
            $arrData[] = [
                'id' => $user->id,
                'owner_name' => ucwords(Helper::getUserMeta($user->id, 'owner_name')) ?: 'Not Yet Added',
                'user_type'=>strcmp($user->roles[0]['name'], 'partner') == 0 ? 'Rental Company' :
                 ucwords($user->roles[0]['name']),
                'company_name' => ucwords(Helper::getUserMeta($user->id, 'company_name')) ?: 'Not Yet Added',
                'mobile' => $user->mobile ? Helper::getUserMeta($user->id, 'user_mobile_country_code') .'&nbsp;'.$user->mobile : 'Not Yet Added',
                'status' => $user->status ?$user->status: 'Not Yet Added',
                'action' => [
                    'edit_url' => route('admin.users.edit', $user->id),
                    'view_url' => route('admin.users.view', $user->id),
                    'delete_url' => route('admin.users.delete', $user->id),
                    'status_change_url'=>route('admin.users.status.update',$user->id),
                ],
            ];
        }
        $response = [
            "draw" => intval($draw),
            "recordsTotal" => $total,
            "recordsFiltered" => $total,
            "data" => $arrData->toArray(),
        ];
        return response()->json($response);
    }



---------------------

 var dataTable = $('#users_list').DataTable({
    // processing: true,
    serverSide: true,
    responsive: false,
    autoWidth: false,
    searching: false,
    sortable:true,
    // ordering:true,
    lengthChange: false,
    info: false,
    order: [[0, "desc"]],
    ajax: {
    url: "{{route('admin.users.list.ajax')}}",
    },
    columns: [
    // { data: 'id', name: 'id', orderable: false, searchable: false },
    { data: 'owner_name', name: 'owner_name', orderable: true  },
    { data: 'user_type', name: 'user_type',orderable: true },
    { data: 'company_name', name: 'company_name',orderable: true },
    { data: 'mobile', name: 'mobile',orderable: true },
    { data: 'status', name: 'status',orderable: true },
    { data: 'action', name: 'action', orderable: false, searchable: false },
    ],
    createdRow: function (row, data, dataIndex) {
        $(row).addClass('bg-white hover:bg-whitesmoke400 text-[#000] lg:border-b lg:borer-b-[#444444]');

        // $(row).find('td:eq(0)').addClass('px-3 py-4 md:py-2.5 md:hidden');
        $(row).find('td:eq(0)').addClass('px-3 pl-5 py-4 md:py-2.5 font-medium text-gray-900 whitespace-nowrap sm:pr-0 sm:pl-[10px] ');
        $(row).find('td:eq(0)').attr('data-view-user-url',data.action.view_url);
        $(row).attr('data-user-id', data.id);
        $('td:eq(0)',row).html(
            ' <div class=""> <div class=" sm:text-sm sm:text-[#000000] sm:font-normal">'+data.owner_name+'</div> <div class="hidden md:block sm:text-xs text-[#444444]">'+data.company_name+' <span class="sm:text-xs md:text-sm sm:block">'+data.mobile+'</span> </div> </div>'
        );

        $(row).find('td:eq(1)').addClass('lg:hidden px-3  py-4');
        $(row).find('td:eq(2)').addClass('lg:hidden px-3  py-4');
        $(row).find('td:eq(3)').addClass('lg:hidden xl:hidden px-3  py-4');
        $(row).find('td:eq(4)').attr('data-view-user-url',data.action.view_url);

        $(row).find('td:eq(4)').addClass(' xl:text-right lg:px-3  py-4 sm:pl-0 sm:pr-[10px]');

        if(window.matchMedia("(max-width: 992px)").matches){
            $(row).find('td:eq(0)').addClass('clickableRow');
            $(row).find('td:eq(4)').addClass('clickableRow');
        }
        // $('td:eq(4)', row).html(
        //         (data.status === 'active' ?
        //             '<div class="status xl:inline-block text-center">'
        //             '<span class=" status_active bg-[#ECF9E2] capitalize">'+ data.status+'</span>' '</div>' :
        //             (data.status === 'deactivate'? '<div class="status xl:inline-block text-center">'
        //             '<span class=" status_active bg-[#ECF9E2] capitalize">'+ data.status+'</span>' '</div>' ):
        //             // '<span class="">'+ data.status+'</span>'
        //         ) +
        // );

        $('td:eq(4)', row).html(
            (data.status === 'active' ?
            '<div class="status xl:inline-block text-center">' +
            '<span class="status_active bg-[#ECF9E2] capitalize lg:text-[13px]">' + data.status + '</span>' + '</div>' :
            (data.status === 'inactive' ? '<div class="status status_inactive xl:inline-block text-center">' +
            '<span class="status_active  capitalize lg:text-[13px]">' + data.status + '</span>' + '</div>' :
            '')));


        $(row).find('td:eq(5)').addClass('pl-3 pr-5 py-4 lg:hidden text-right md:py-2.5 md:pr-3 ');
        $('td:eq(5)', row).html(
            '<div class="action_sec_view">' +
            '<a href="' + data.action.edit_url + '" class="links_item_cta mr-2 dash_circle desh_edit_bg font-medium text-gray-600 hover:underline">' +
            '<img src="{{asset('images/edit_icon.svg')}}" alt="Edit">' +
            '<span class="tooltiptext">Edit</span>' +
            '</a>' +
            '<a href="' + data.action.view_url + '" class="links_item_cta mr-2 dash_circle desh_view_bg font-medium text-gray-600 hover:underline">' +
            '<img src="{{asset('images/eye.svg')}}" alt="View">' +
            '<span class="tooltiptext">View</span>' +
            '</a>' +
            '<div class=" relative  triple_dots_main flex pt-2 pb-2 rounded-t border border-transparent"> <a href="javascript:void(0);" class=" relative  triple_dots_action_btn triple_dots ">' +
            '<img src="{{asset('images/triple_dottts.svg')}}" alt="More Options">' +
            '</a>' +
            ' <div class="dots_hover_sec list_link_frame_section top-[42px] absolute w-[165px] border border-[#D1D1D1] rounded-[5px] rounded-tr-none py-[15px] bg-[#fff] z-[2] -left-[129px] custom-shadow afclr hidden"> <ul class="frame_list_items_popup">' +
            ' <li class="text-left"><a  href="javascript:void(0);" data-user-id="'+data.id+'" data-delete-url="' + data.action.delete_url + '" class="pl-[15px] delete_user  capitalize inline-block w-full py-2 hover:bg-siteYellow text-[#000] duration-300" id="" >delete user</a>' + '</li>'+
            ' <li class="text-left"><a data-src="#change_status_popup" data-fancybox href="javascript:void(0);" class=" pl-[15px] change_status_user capitalize inline-block w-full py-2 hover:bg-siteYellow text-[#000] duration-300" data-user-id="'+data.id+'" data-status-change-url="'+data.action.status_change_url+'" data-user-status="'+data.status+'" >Change Status</a>'  + '</li>'+
            ' <li class="text-left"><a  href="javascript:void(0);" class="pl-[15px] change_subscription_user capitalize inline-block w-full py-2 hover:bg-siteYellow text-[#000] duration-300" id="" >Change Subscription</a>' + '</li>'+
            '</ul> </div>' +
            '</div>' +
            '</div>'
        );
    },
    language:{
        oPaginate:{
        sPrevious: '<span class="hidden pagination_link" aria-hidden="true">\
    <svg width="40" height="15" viewBox="0 0 40 15" fill="none" xmlns="http://www.w3.org/2000/svg">\
        <path fill-rule="evenodd" clip-rule="evenodd"\
            d="M8.4799 0.000511718C8.5734 0.00614315 8.663 0.0401363 8.73686 0.0980374C8.81072 0.155939 8.86536 0.235024 8.89357 0.324802C8.92178 0.414581 8.92222 0.510847 8.89484 0.600884C8.86746 0.690921 8.81355 0.770484 8.74022 0.829069L1.71152 6.91993H39.5306C39.5919 6.91905 39.6528 6.93044 39.7097 6.95343C39.7666 6.97641 39.8184 7.01054 39.8621 7.05382C39.9058 7.0971 39.9405 7.14868 39.9641 7.20555C39.9878 7.26242 40 7.32345 40 7.3851C40 7.44674 39.9878 7.50778 39.9641 7.56465C39.9405 7.62152 39.9058 7.67309 39.8621 7.71637C39.8184 7.75965 39.7666 7.79378 39.7097 7.81677C39.6528 7.83975 39.5919 7.85114 39.5306 7.85027H1.63923L8.37864 14.1882C8.42377 14.2301 8.46021 14.2805 8.48586 14.3366C8.51151 14.3927 8.52588 14.4533 8.52811 14.515C8.53035 14.5767 8.52043 14.6382 8.49891 14.696C8.47739 14.7538 8.4447 14.8068 8.40273 14.8519C8.36076 14.8969 8.31033 14.9332 8.25435 14.9586C8.19837 14.984 8.13795 14.998 8.07656 14.9998C8.01518 15.0016 7.95404 14.9912 7.89667 14.9692C7.8393 14.9472 7.78684 14.9139 7.7423 14.8714L0.149597 7.73397C0.101248 7.6893 0.0629115 7.63479 0.0371357 7.57407C0.0113599 7.51336 -0.00126492 7.4478 9.99709e-05 7.3818C0.00146486 7.3158 0.0167883 7.25085 0.0450521 7.19127C0.0733158 7.13168 0.113872 7.07884 0.164027 7.03622L8.14724 0.116804C8.22739 0.0456103 8.3296 0.00451701 8.43649 0.000511718C8.45095 -0.000170573 8.46544 -0.000170573 8.4799 0.000511718Z"\
            fill="black" />\
    </svg>\
    <span class="page_name hidden sm:hidden ">Prev</span>\
    <span class="" aria-disabled="true" aria-label="« Previous">\
    </span>\
    </span>',
    sNext: '<span class="pagination_link hidden">\
    <span class="page_name hidden sm:hidden  ">Next</span>\
    <svg width="40" height="15" viewBox="0 0 40 15" fill="none" xmlns="http://www.w3.org/2000/svg">\
        <path fill-rule="evenodd" clip-rule="evenodd"\
        d="M31.5201 0.000511718C31.4266 0.00614315 31.337 0.0401363 31.2631 0.0980374C31.1893 0.155939 31.1346 0.235024 31.1064 0.324802C31.0782 0.414581 31.0778 0.510847 31.1052 0.600884C31.1325 0.690921 31.1865 0.770484 31.2598 0.829069L38.2885 6.91993H0.469383C0.408058 6.91905 0.347172 6.93044 0.290264 6.95343C0.233353 6.97641 0.181557 7.01054 0.137882 7.05382C0.0942078 7.0971 0.0595284 7.14868 0.0358582 7.20555C0.012188 7.26242 0 7.32345 0 7.3851C0 7.44674 0.012188 7.50778 0.0358582 7.56465C0.0595284 7.62152 0.0942078 7.67309 0.137882 7.71637C0.181557 7.75965 0.233353 7.79378 0.290264 7.81677C0.347172 7.83975 0.408058 7.85114 0.469383 7.85027H38.3608L31.6214 14.1882C31.5762 14.2301 31.5398 14.2805 31.5141 14.3366C31.4885 14.3927 31.4741 14.4533 31.4719 14.515C31.4696 14.5767 31.4796 14.6382 31.5011 14.696C31.5226 14.7538 31.5553 14.8068 31.5973 14.8519C31.6392 14.8969 31.6897 14.9332 31.7456 14.9586C31.8016 14.984 31.862 14.998 31.9234 14.9998C31.9848 15.0016 32.046 14.9912 32.1033 14.9692C32.1607 14.9472 32.2132 14.9139 32.2577 14.8714L39.8504 7.73397C39.8988 7.6893 39.9371 7.63479 39.9629 7.57407C39.9886 7.51336 40.0013 7.4478 39.9999 7.3818C39.9985 7.3158 39.9832 7.25085 39.9549 7.19127C39.9267 7.13168 39.8861 7.07884 39.836 7.03622L31.8528 0.116804C31.7726 0.0456103 31.6704 0.00451701 31.5635 0.000511718C31.549 -0.000170573 31.5346 -0.000170573 31.5201 0.000511718Z"\
        fill="black" />\
    </svg>\
    </span>',
        sFirst: '',
        sLast: ''
        }
    },
    drawCallback: function(settings) {
        var api = this.api();
        var recordsTotal = api.page.info().recordsTotal;
        if (recordsTotal > 10) {
            $('#' + api.table().node().id + '_paginate').show();
        } else {
            $('#' + api.table().node().id + '_paginate').hide();
        }
    }
    });

    dataTable.on('preXhr.dt', function ( e, settings, data ) {
            $(".loader").css("display", "inline-flex");
            $(".overlay_sections").css("display", "block");
            }).on('draw.dt', function () {
            $(".loader").css("display", "none");
            $(".overlay_sections").css("display", "none");
    });



