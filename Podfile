# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'

target 'nOcAp' do
  use_frameworks!
    pod 'TriumphSDK'

end

target 'nOcAp MessagesExtension' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!
    pod 'TriumphSDK'

  # Pods for nOcAp MessagesExtension

end

plugin 'cocoapods-triumph-sdk-plugin'
post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      # Feel free to change it from 14.0 to whatever minimum version do you use for your application
      # This will remove all of the CocoaPods dependencies warnings regarding minimum iOS version
      if config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'].to_f < 14.0
        config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '14.0'
      end
      
      # Unfortunately, when using .xcframeworks like our application, CocoaPods does not set this flag by default
      # Thus, this leads to a linkage error, and this setting is required
      config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
      
      # We're using some dependencies that contain bundles which by default are set to be resigned
      # This is required to make your build successful
      if target.respond_to?(:product_type) and target.product_type == "com.apple.product-type.bundle"
        config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      end
    end
  end
end
