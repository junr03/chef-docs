.. This is an included how-to. 

The following is an example of using the ``platform_family?`` method in the |dsl recipe| to create a variable that can be used with other resources in the same recipe. In this example, ``platform_family?`` is being used to ensure that a specific binary is used for a specific platform before using the |resource remote_file| resource to download a file from a remote location, and then using the |resource execute| resource to install that file by running a command.

.. code-block:: ruby

   if platform_family?("rhel")
     pip_binary = "/usr/bin/pip"
   else
     pip_binary = "/usr/local/bin/pip"
   end
   
   remote_file "#{Chef::Config[:file_cache_path]}/distribute_setup.py" do
     source "http://python-distribute.org/distribute_setup.py"
     mode '0644'
     not_if { ::File.exists?(pip_binary) }
   end
   
   execute "install-pip" do
     cwd Chef::Config[:file_cache_path]
     command <<-EOF
       # command for installing Python goes here
       EOF
     not_if { ::File.exists?(pip_binary) }
   end

where a command for installing |python| might look something like:

.. code-block:: ruby

    #{node['python']['binary']} distribute_setup.py
    #{::File.dirname(pip_binary)}/easy_install pip
