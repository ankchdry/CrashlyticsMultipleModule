# Uncomment the next line to define a global platform for your project
platform :ios, '13.2'

project 'CrashlyticsMultipleModule.xcodeproj'
workspace 'CrashlyticsMultipleModule.xcworkspace'

def networking_pod
  pod 'Networking', :path => 'DevPods/Networking'
end

def development_pods
  networking_pod
end

def firebase_stack
  pod 'Firebase/Analytics'
  pod 'Firebase/Crashlytics'
end

target 'CrashlyticsMultipleModule' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!
  
  networking_pod
  firebase_stack
end

target 'Networking_Example' do
  use_frameworks!
  project 'Devpods/Networking/Example/Networking.xcodeproj'
  networking_pod  
end

swift_versions_of_pods = {
  'Networking_Example' => '4.2'
}

post_install do |installer|
  installer.pods_project.targets.each do |target|
    defined_swift_version = swift_versions_of_pods[target.name]
    next if defined_swift_version.blank?
    target.build_configurations.each do |config|
      config.build_settings['SWIFT_VERSION'] = defined_swift_version
    end
  end
end

