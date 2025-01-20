# What is the problem being solved?

The demonstration of a general-purpose, multi-user, interactive operating system that is neither expensive in equipment (hardware) nor human effort (human-years required to build the OS). In addition, the OS is simple, elegant and easy-to-use.

# How was this problem solved previously?

The paper does not have a section on this. However, it is implied that previous efforts have much larger-sized (number of lines) operating system and are expensive in either hardware equipment required or human effort to build it. They also do not usually come with hierarchical file system or an interactive command line interpreter (lack of convenient features). Files and devices are also treated differently (inelegant design). Links in directories have different statuses (3.2), making for relatively inelegant and inefficient design.

# What is the main idea?

The main idea is to make the OS simple, elegant and easy-to-use, which is achieved through several good design choices. Firstly, UNIX has a hierarchical file system with demountable volumes (convenient, reduces size of OS). Secondly, it provides the same abstraction for files and devices i.e. it "pushes all device-dependent considerations into the OS itself" (8). Thirdly, the paper describes how everything originates from the init process through several process function calls (elegance, simplicity, small code size). Lastly, it provides a command-line interpreter for ease of use by programmers.

# What are the key results?

The efficiency of the file system is tested (4.1), to which the authors said they are "generally satisfied with the overall performance of the system". They showed some statistics on the usage of a computer per day, CPU accesses, command accesses (9.2) to illustrate the scale at which the OS is operating in. They also include a section on reliability.

# What are the main limitations of this paper?

The main limitation is that it did not show any comparison with other existing operating systems. Perhaps the authors felt that there are no basis of comparison, but an indication of the existing hardware cost and codebase size will provide some reference. There is no efficiency comparison as well, so readers might not be fully convinced by the efficiency of the file system (4.1).

# Why did this paper have an impact?

The proposed operating system is very general purposed in nature. The authors designed UNIX in a way such that users are comfortable with the machine and can explore/invent easily in the operating system space. The interactive use (Shell) made it convenient for programmers. The design is also elegant. Because of these, I think the general programming population liked it a lot. The smaller scale and cost also meant more people can have access to it.

