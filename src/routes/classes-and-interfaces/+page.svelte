<script lang="ts">
    abstract class Department {
        static fiscalYear = 2023;
        // private readonly id: string;
        // private name: string;
        protected employees: string[] = []

        constructor(protected readonly id: string, public name: string) {
            // this.id = id;
            // this.name = n;
        }

        static createEmployee(name: string) {
            return { name: name }
        }

        abstract describe(this: Department): void;

        addEmployee(employee: string): void {
            // this.id = 'd2'; // its a readonly property
            this.employees.push(employee);
        }

        printEmployeeInformation() {
            console.log(this.employees.length);
            console.log(this.employees);
        }
    }

    const employee1 = Department.createEmployee('Ondrej');
    console.log(employee1, Department.fiscalYear)

    class ITDepartment extends Department {
        constructor(id: string, public admins: string[]) {
            super(id, 'IT');
        }

        describe() {
            console.log('Accounting Department - ID: ' + this.id);
        }
    }

    class AccountingDepartment extends Department {
        private lastReport: string;

        get mostRecentReport() {
            if (this.lastReport) {
                return this.lastReport;
            }
            throw new Error('No report found.');
        }

        set mostRecentReport(value: string) {
            if (!value) {
                throw new Error('Please pass in a valid value!');
            }
            this.addReport(value);
        }

        constructor(id: string, private reports: string[]) {
            super(id, 'IT');
            this.lastReport = reports[0];
        }

        describe() {
            console.log('Accounting Department - ID: ' + this.id);
        }

        addEmployee(name: string) {
            if (name === 'Max') {
                return;
            }
            this.employees.push(name);
        }

        addReport(text: string) {
            this.reports.push(text);
            this.lastReport = text;
        }

        printReports() {
            console.log(this.reports)
        }
    }

    const it = new ITDepartment('d1', ['Max']);

    it.addEmployee('Max')
    it.addEmployee('Manu')

    // it.employees[2] = 'Anna' // not working bacause its private

    it.describe();
    it.printEmployeeInformation();

    console.log(it)

    const accounting = new AccountingDepartment('d2', []);

    accounting.mostRecentReport = 'Year End Report';
    accounting.addReport('Something went wrong...')
    console.log(accounting.mostRecentReport)


    accounting.addEmployee('Max')
    accounting.addEmployee('Manu')

    // accounting.printReports()
    // accounting.printEmployeeInformation();

    accounting.describe();

    // const accountingCopy = { name: 'DUMMY', describe: accounting.describe };
    // accountingCopy.describe(); // not working bacause there are not filled all the properties

</script>

<h5>Classes and Interfaces</h5>