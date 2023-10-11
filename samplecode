using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace JenkinsPipelineExample
{
    class Program
    {
        static void Main(string[] args)
        {
            // Build the project
            msbuild

            // Run the unit tests
            nunit

            // Generate a test report
            nunit-console --result:TestResult.xml

            // Perform SonarQube code scanning
            sonar-scanner
        }
    }
}
