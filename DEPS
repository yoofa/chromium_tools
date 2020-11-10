use_relative_paths = True

vars = {
  'chromium_url': 'https://chromium.googlesource.com',

  #
  # TODO(crbug.com/941824): The values below need to be kept in sync
  # between //DEPS and //buildtools/DEPS, so if you're updating one,
  # update the other. There is a presubmit check that checks that
  # you've done so; if you are adding new tools to //buildtools and
  # hence new revisions to this list, make sure you update the
  # _CheckBuildtoolsRevsAreInSync in PRESUBMIT.py to include the additional
  # revisions.
  #

  # GN CIPD package version.
  'gn_version': 'git_revision:7d7e8deea36d126397bda2cf924682504271f0e1',

  # When changing these, also update the svn revisions in deps_revisions.gni
  'clang_format_revision': '96636aa0e9f047f17447f2d45a094d0b59ed7917',
  'libcxx_revision':       'd9040c75cfea5928c804ab7c235fed06a63f743a',
  'libcxxabi_revision':    '196ba1aaa8ac285d94f4ea8d9836390a45360533',
  'libunwind_revision':    'd999d54f4bca789543a2eb6c995af2d9b5a1f3ed',
}

deps = {
  'chromium_tools/buildtools':                                                                                 
    'https://chromium.googlesource.com/chromium/src/buildtools@1ed99573d57d4b6041261b531cdf876e631cf0bc',

  'chromium_tools/buildtools/linux64': {                                                                       
    'packages': [                                                                                   
      {                                                                                             
        'package': 'gn/gn/linux-amd64',                                                             
        'version': 'git_revision:7d7e8deea36d126397bda2cf924682504271f0e1',                         
      }                                                                                             
    ],                                                                                              
    'dep_type': 'cipd',                                                                             
    'condition': 'checkout_linux',                                                                  
  },                                                                                                
  'chromium_tools/buildtools/mac': {                                                                           
    'packages': [                                                                                   
      {                                                                                             
        'package': 'gn/gn/mac-amd64',                                                               
        'version': 'git_revision:7d7e8deea36d126397bda2cf924682504271f0e1',                         
      }                                                                                             
    ],                                                                                              
    'dep_type': 'cipd',                                                                             
    'condition': 'checkout_mac',                                                                    
  },                                                                                                
  'chromium_tools/buildtools/win': {                                                                           
    'packages': [                                                                                   
      {                                                                                             
        'package': 'gn/gn/windows-amd64',                                                           
        'version': 'git_revision:7d7e8deea36d126397bda2cf924682504271f0e1',                         
      }                                                                                             
    ],                                                                                              
    'dep_type': 'cipd',                                                                             
    'condition': 'checkout_win',                                                                    
  },                                                                                                
                                                                                                    
  'chromium_tools/buildtools/clang_format/script':                                                             
    'https://chromium.googlesource.com/chromium/llvm-project/cfe/tools/clang-format.git@96636aa0e9f047f17447f2d45a094d0b59ed7917',
  'chromium_tools/buildtools/third_party/libc++/trunk':                                                        
    'https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libcxx.git@d9040c75cfea5928c804ab7c235fed06a63f743a',
  'chromium_tools/buildtools/third_party/libc++abi/trunk':                                                     
    'https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libcxxabi.git@196ba1aaa8ac285d94f4ea8d9836390a45360533',
  'chromium_tools/buildtools/third_party/libunwind/trunk':                                                     
    'https://chromium.googlesource.com/external/github.com/llvm/llvm-project/libunwind.git@d999d54f4bca789543a2eb6c995af2d9b5a1f3ed',


  hooks = [
  # Pull clang-format binaries using checked-in hashes.                                             
  {                                                                                                 
    'name': 'clang_format_win',                                                                     
    'pattern': '.',                                                                                 
    'condition': 'host_os == "win"',                                                                
    'action': [ 'download_from_google_storage',                                                     
                '--no_resume',                                                                      
                '--platform=win32',                                                                 
                '--no_auth',                                                                        
                '--bucket', 'chromium-clang-format',                                                
                '-s', 'src/buildtools/win/clang-format.exe.sha1',                                   
    ],                                                                                              
  },                                                                                                
  {                                                                                                 
    'name': 'clang_format_mac',                                                                     
    'pattern': '.',                                                                                 
    'condition': 'host_os == "mac"',                                                                
    'action': [ 'download_from_google_storage',                                                     
                '--no_resume',                                                                      
                '--platform=darwin',                                                                
                '--no_auth',                                                                        
                '--bucket', 'chromium-clang-format',                                                
                '-s', 'src/buildtools/mac/clang-format.sha1',                                       
    ],                                                                                              
  },                                                                                                
  {                                                                                                 
    'name': 'clang_format_linux',                                                                   
    'pattern': '.',                                                                                 
    'condition': 'host_os == "linux"',                                                              
    'action': [ 'download_from_google_storage',                                                     
                '--no_resume',                                                                      
                '--platform=linux*',                                                                
                '--no_auth',                                                                        
                '--bucket', 'chromium-clang-format',                                                
                '-s', 'src/buildtools/linux64/clang-format.sha1',                                   
    ],                                                                                              
  },  
  ]
}
