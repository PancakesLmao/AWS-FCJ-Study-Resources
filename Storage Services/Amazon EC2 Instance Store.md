#storage #services 
An instance store provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. An instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content

# Persistent Volumes
Instance store volumes **ARE NOT PERSISTENT storage**. If your instance is (on purpose or by system failure) stopped, hibernated, or terminated, you will lose all your data on the volume
# Limited Availability 
Instance store volumes have **LIMTED availability** because they are only optional for a certain combination of AMIs and instance types. When selecting an AMI, you can filter for AMIs that offer instance store volumes
# Add Volumes
You can specify instance store volumes for an instance only when you launch it. After the instance is launched, you can add EBS volumes to the instance but not instance store volumes
# Detach Volumes
An instance store volume's disk are physically attached to the instance. Therefore, you **CANNOT detach** an instance store volume from one instance and attach it to another instance. AWS does not offer you the option to detach the volume
# Configure Volume
Instance store volumes **ARE NOT configurable**. The instance type that you choose predetermines the volume type (SSD or HDD) and size. These configuration **ARE NOT optional**. You also **CANNOT encrypt** these volumes